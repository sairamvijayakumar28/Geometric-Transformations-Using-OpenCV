# Geometric Transformations Using OpenCV

---

## Aim

To write a Python program using OpenCV to perform various geometric transformations on an image.

The program performs the following operations:

- Image Translation  
- Image Scaling (Resizing)  
- Image Shearing  
- Image Reflection (Flipping)  
- Image Rotation  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image in color mode.

### Step 3: Image Translation
- Create a translation matrix to shift the image  
- Move the image 50 pixels to the right and 80 pixels down  
- Apply transformation using `cv2.warpAffine()`  
- Display original and translated images  

### Step 4: Image Scaling
- Resize the image to 0.5× (downscale)  
- Resize the image to 2× (upscale)  
- Use `cv2.resize()`  
- Display original, downscaled, and upscaled images  

### Step 5: Image Shearing
- Create transformation matrices for:
  - Horizontal shearing  
  - Vertical shearing  
- Apply transformations using `cv2.warpAffine()`  
- Display original and sheared images  

### Step 6: Image Reflection
- Perform flipping using `cv2.flip()`:
  - Horizontal reflection  
  - Vertical reflection  
  - Both axes  
- Display all reflected images  

### Step 7: Image Rotation
- Create rotation matrices for:
  - 45° rotation  
  - 90° rotation  
- Use `cv2.getRotationMatrix2D()` and `cv2.warpAffine()`  
- Display original and rotated images  

---

##  Program

### Developed By:
**Name:** Sairam V
### Register No: 212225230237

```
# Import 

import cv2
import numpy as np
import matplotlib.pyplot as plt
# Read the image using OpenCV

image = cv2.imread('baseball.jpg')
image.shape
plt.imshow(image[:,:,::-1])
plt.title('Original Image')
plt.show()
tx, ty = 100, 200
M_translation = np.float32([[1, 0, tx],[0, 1, ty]])
translated_image = cv2.warpAffine(image, M_translation,(image.shape[1], image.shape[0]))
plt.figure(figsize=(10,5))

plt.subplot(1,2,1)
plt.imshow(image[:,:,::-1])
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,2,2)
plt.imshow(translated_image[:,:,::-1])
plt.title("Translated Image")
plt.axis("off")

plt.show()
image = cv2.imread("baseball.jpg")
downscaled_image = cv2.resize(image, None,fx=0.25,fy=0.25,interpolation=cv2.INTER_LINEAR)
upscaled_image = cv2.resize(image, None,fx=3,fy=3,interpolation=cv2.INTER_LINEAR)
plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(image[:,:,::-1])
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(downscaled_image[:,:,::-1])
plt.title("Downscaled Image")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(upscaled_image[:,:,::-1])
plt.title("Upscaled Image")
plt.axis("off")

plt.show()
horizontal_matrix = np.float32([[1,0.5,0],[0,1,0]])
horizontal_shear = cv2.warpAffine(image,horizontal_matrix,(image.shape[1], image.shape[0]))
vertical_matrix = np.float32([[1,0,0],[0.5,1,0]])
vertical_shear = cv2.warpAffine(image,vertical_matrix,(image.shape[1], image.shape[0]))

plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(image[:,:,::-1])
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(horizontal_shear[:,:,::-1])
plt.title("Horizontal Shear")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(vertical_shear[:,:,::-1])
plt.title("Vertical Shear")
plt.axis("off")

plt.show()
horizontal = cv2.flip(image,1)
vertical = cv2.flip(image,0)
both = cv2.flip(image,-1)
plt.figure(figsize=(10,10))

plt.subplot(2,2,1)
plt.imshow(image[:,:,::-1])
plt.title("Original Image")
plt.axis("off")

plt.subplot(2,2,2)
plt.imshow(horizontal[:,:,::-1])
plt.title("Horizontal Reflection")
plt.axis("off")

plt.subplot(2,2,3)
plt.imshow(vertical[:,:,::-1])
plt.title("Vertical Reflection")
plt.axis("off")

plt.subplot(2,2,4)
plt.imshow(both[:,:,::-1])
plt.title("Both Axes Reflection")
plt.axis("off")

plt.show()
(height, width) = image.shape[:2]

center = (width//2, height//2)
matrix45 = cv2.getRotationMatrix2D(center,45,1)
rotate45 = cv2.warpAffine(image,matrix45,(width,height))
matrix90 = cv2.getRotationMatrix2D(center,90,1)
rotate90 = cv2.warpAffine(image,matrix90,(width,height))
plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(image[:,:,::-1])
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(rotate45[:,:,::-1])
plt.title("45 Degree Rotation")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(rotate90[:,:,::-1])
plt.title("90 Degree Rotation")
plt.axis("off")

plt.show()
```
---

##  Output

<img width="690" height="426" alt="image" src="https://github.com/user-attachments/assets/dfa66b95-88c5-44a7-90d6-7dfa54d0cf1b" />

<img width="702" height="235" alt="image" src="https://github.com/user-attachments/assets/870791d5-e58c-4337-b37a-58bca73a6779" />


<img width="1443" height="318" alt="image" src="https://github.com/user-attachments/assets/6daaadc3-7ea2-406e-b3f5-63976a896363" />



<img width="1488" height="295" alt="image" src="https://github.com/user-attachments/assets/bbde37cc-78c2-48a8-872a-c6f192d4658b" />


<img width="1409" height="424" alt="image" src="https://github.com/user-attachments/assets/5b38c21d-6e77-498e-84dc-e94e0c0cd22e" />


<img width="1446" height="525" alt="image" src="https://github.com/user-attachments/assets/fce087af-c175-4eb6-821b-2a8329be42a1" />


<img width="1437" height="346" alt="image" src="https://github.com/user-attachments/assets/647f0a3d-8dee-48c2-acfe-864cfd15b779" />

### Image Translation
- Original image is displayed  
- Translated image (shifted right and down) is displayed  

### Image Scaling
- Original image is displayed  
- Downscaled image (0.5×) is displayed  
- Upscaled image (2×) is displayed  

### Image Shearing
- Original image is displayed  
- Horizontally sheared image is displayed  
- Vertically sheared image is displayed  

### Image Reflection
- Original image is displayed  
- Horizontally flipped image is displayed  
- Vertically flipped image is displayed  
- Both-axis flipped image is displayed  

### Image Rotation
- Original image is displayed  
- 45° rotated image is displayed  
- 90° rotated image is displayed  

---

##  Result

Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.
