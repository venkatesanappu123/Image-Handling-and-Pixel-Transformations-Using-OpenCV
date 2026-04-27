# Image-Handling-and-Pixel-Transformations-Using-OpenCV 

## AIM:
Write a Python program using OpenCV that performs the following tasks:

1) Read and Display an Image.  
2) Adjust the brightness of an image.  
3) Modify the image contrast.  
4) Generate a third image using bitwise operations.

## Software Required:
- Anaconda - Python 3.7
- Jupyter Notebook (for interactive development and execution)

## Algorithm:
### Step 1:
Load an image from your local directory and display it.

### Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.  
Display the original, brighter, and darker images.

### Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).  
Display the original, lower contrast, and higher contrast images.

### Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels

## Program Developed By:
- **Name:** VENKATESAN R 
- **Register Number:** 212224230299

  ### Ex. No. 01

#### 1. Read the image ('Eagle_in_Flight.jpg') using OpenCV imread() as a grayscale image.
```python
img_bgr = cv2.imread("Eagle_in_Flight.jpg",0)
```

#### 2. Print the image width, height & Channel.
```python
img_bgr.shape
```

#### 3. Display the image using matplotlib imshow().
```python
plt.imshow(img_bgr,cmap="gray")
plt.title("OUTPUT GRAYSCALE IMAGE")
plt.axis("off")
plt.show()
```

#### 4. Save the image as a PNG file using OpenCV imwrite().
cv2.imwrite("Gray_Image.jpg",img_bgr)
```

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```python
img_rgb = cv2.cvtColor(img_bgr, cv2.COLOR_BGR2RGB)
```

#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```python
plt.imshow(img_rgb)
plt.axis("on")
img_bgr.shape
```

#### 7. Crop the image to extract any specific (Eagle alone) object from the image.
```python
cropped_img=img_rgb[20:420,180:550]
plt.figure(figsize=[10,8])
plt.subplot(121);plt.imshow(img_rgb);plt.title("Original Image");plt.axis("off")
plt.subplot(122);plt.imshow(cropped_img);plt.title("Cropped Image");plt.axis("off")
plt.show()
```

#### 8. Resize the image up by a factor of 2x.
```python
res = cv2.resize(cropped_img,(200*2, 200*2))
```

#### 9. Flip the cropped/resized image horizontally.
```python
flip= cv2.flip(res,1)
plt.imshow(flip[:,:,::-1])
plt.title("Flipped Horizontally")
plt.axis("off")
```

#### 10. Read in the image ('Apollo-11-launch.jpg').
```python
img=cv2.imread("Apollo-11-launch.jpg",1)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
img_rgb.shape
```

#### 11. Add the following text to the dark area at the bottom of the image (centered on the image):
```python
text = cv2.putText(img_rgb, "Apollo 11 Saturn V Launch, July 16, 1969", (300, 700),
cv2.FONT_HERSHEY_SIMPLEX, 1, (255, 255, 255), 2)  
plt.imshow(text, cmap='gray')  
plt.title("New image")
plt.show()
```

#### 12. Draw a magenta rectangle that encompasses the launch tower and the rocket.
```python
rcol= (255, 0, 255)
cv2.rectangle(img_rgb, (400, 100), (800, 650), rcol, 3)  
```

#### 13. Display the final annotated image.
```python
plt.title("Annotated image")
plt.imshow(img_rgb)
plt.show()
```

#### 14. Read the image ('Boy.jpg').
```python
img =cv2.imread('boy.jpg',cv2.IMREAD_COLOR)
img_rgb= cv2.cvtColor(img, cv2.COLOR_BGR2RGB) 
```

#### 15. Adjust the brightness of the image.
```python
m = np.ones(img_rgb.shape, dtype="uint8") * 50
```

#### 16. Create brighter and darker images.
```python
img_brighter = cv2.add(img_rgb, m)  
img_darker = cv2.subtract(img_rgb, m) 
```

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```python
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(img_rgb), plt.title("Original Image"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(img_brighter), plt.title("Brighter Image"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(img_darker), plt.title("Darker Image"), plt.axis("off")
plt.show()
```

#### 18. Modify the image contrast.
```python
matrix1 = np.ones(img_rgb.shape, dtype="float32") * 1.1
matrix2 = np.ones(img_rgb.shape, dtype="float32") * 1.2
img_higher1 = cv2.multiply(img.astype("float32"), matrix1).clip(0,255).astype("uint8")
img_higher2 = cv2.multiply(img.astype("float32"), matrix2).clip(0,255).astype("uint8")
```

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```python
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(img), plt.title("Original Image"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(img_higher1), plt.title("Higher Contrast (1.1x)"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(img_higher2), plt.title("Higher Contrast (1.2x)"), plt.axis("off")
plt.show()
```

#### 20. Split the image (boy.jpg) into the B,G,R components & Display the channels.
```python
b, g, r = cv2.split(img)
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(b, cmap='gray'), plt.title("Blue Channel"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(g, cmap='gray'), plt.title("Green Channel"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(r, cmap='gray'), plt.title("Red Channel"), plt.axis("off")
plt.show()
```

#### 21. Merged the R, G, B , displays along with the original image
```python
merged_rgb = cv2.merge([r, g, b])
plt.figure(figsize=(5,5))
plt.imshow(merged_rgb)
plt.title("Merged RGB Image")
plt.axis("off")
plt.show()
```

#### 22. Split the image into the H, S, V components & Display the channels.
```python
hsv_img = cv2.cvtColor(img, cv2.COLOR_RGB2HSV)
h, s, v = cv2.split(hsv_img)
plt.figure(figsize=(10,5))
plt.subplot(1,3,1), plt.imshow(h, cmap='gray'), plt.title("Hue Channel"), plt.axis("off")
plt.subplot(1,3,2), plt.imshow(s, cmap='gray'), plt.title("Saturation Channel"), plt.axis("off")
plt.subplot(1,3,3), plt.imshow(v, cmap='gray'), plt.title("Value Channel"), plt.axis("off")
plt.show()
```
#### 23. Merged the H, S, V, displays along with original image.
```python
merged_hsv = cv2.cvtColor(cv2.merge([h, s, v]), cv2.COLOR_HSV2RGB)
combined = np.concatenate((img_rgb, merged_hsv), axis=1)
plt.figure(figsize=(10, 5))
plt.imshow(combined)
plt.title("Original Image  &  Merged HSV Image")
plt.axis("off")
plt.show()
```

## Output:
i) Read and Display an Image. 1.Read 'Eagle_in_Flight.jpg' as grayscale and display:

<img width="318" height="266" alt="{4ADDA5AE-47C0-4909-BBFE-9FE96F6978FF}" src="https://github.com/user-attachments/assets/97bbdc89-bc96-4789-b35b-360c6202faa6" />

2.Save image as PNG and display:

<img width="535" height="442" alt="image" src="https://github.com/user-attachments/assets/23d0fd97-effa-4bf6-86c5-a7733eac2ddb" />

3.Cropped image:

<img width="812" height="428" alt="image" src="https://github.com/user-attachments/assets/990497a0-dff1-4161-9e20-d476228ef3fb" />

4.Resize and flip Horizontally:

<img width="392" height="412" alt="image" src="https://github.com/user-attachments/assets/c86dca0c-27a1-4944-982d-4aac12b1cc17" />

5.Read 'Apollo-11-launch.jpg' and Display the final annotated image:

<img width="561" height="337" alt="image" src="https://github.com/user-attachments/assets/097b4f8a-03fe-48b1-9122-a649ad1db563" />

ii) Adjust Image Brightness.

1.Create brighter and darker images and display:

<img width="802" height="217" alt="image" src="https://github.com/user-attachments/assets/4420d2b4-e17e-4e64-b6d7-f698f1779850" />

iii) Modify Image Contrast.

1.Modify contrast using scaling factors 1.1 and 1.2

<img width="798" height="215" alt="image" src="https://github.com/user-attachments/assets/440d78cc-f811-42e4-80e1-d5a009ddefbe" />

iv) Generate Third Image Using Bitwise Operations.

1.Split 'Boy.jpg' into B, G, R components and display:

<img width="795" height="211" alt="image" src="https://github.com/user-attachments/assets/126aa02e-e484-4b5d-8fa6-36902ab22e7e" />

2.Merge the R, G, B channels and display:

<img width="402" height="328" alt="image" src="https://github.com/user-attachments/assets/7eb6e000-c6a4-4b9b-ae11-089e82baf99f" />

3.Split the image into H, S, V components and display:

<img width="792" height="217" alt="image" src="https://github.com/user-attachments/assets/41eec967-5757-47bf-8cdd-d14254286f0e" />

4.Merge the H, S, V channels and display:

<img width="797" height="307" alt="image" src="https://github.com/user-attachments/assets/f0bfd3ae-0ea9-4363-a0d2-4f54a94ebad9" />

## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.

