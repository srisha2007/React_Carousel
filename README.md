# Ex05 Image Carousel
## Date:27/05/2026

## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM
APP.JSX
```
import { useState, useEffect } from "react";
import "./App.css";

import sun from "./assets/sun.png";
import moon from "./assets/moon.png";
import earth from "./assets/earth.png";

function App() {
  const images = [
    { src: sun, alt: "Sun" },
    { src: moon, alt: "Moon" },
    { src: earth, alt: "Earth" },
  ];

  const [currentIndex, setCurrentIndex] = useState(0);

  useEffect(() => {
    const interval = setInterval(() => {
      setCurrentIndex((prev) => (prev + 1) % images.length);
    }, 3000);
    return () => clearInterval(interval);
  }, []);

  return (
    <div className="carousel">
        <h1>   Solar Carousel 🌞🌙🌍</h1>
      <div className="image-container">
        <img
          src={images[currentIndex].src}
          alt={images[currentIndex].alt}
          className="fade"
        />
      </div>
      <div className="dots">
        {images.map((_, index) => (
          <span
            key={index}
            className={index === currentIndex ? "dot active" : "dot"}
            onClick={() => setCurrentIndex(index)}
          ></span>
        ))}
      </div>
    </div>
  );
}

export default App;
```

APP.CSS
```
/* Center everything on the page */
.carousel {
  background-color: #13cbe7;
  color: white;
  height: 100vh;
  width: 100vw;
  display: flex;
  flex-direction: column;
  justify-content: center; /* vertical center */
  align-items: center; /* horizontal center */
  text-align: center;
  overflow: hidden;
  margin: 0;
}

/* Title styling */
.carousel h1 {
  font-size: 2.5rem;
  margin-bottom: 20px;
  font-weight: bold;
}

/* Image box styling */
.image-container {
  width: 400px;
  height: 400px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 0 30px rgba(88, 118, 213, 0.3);
}

/* Image fit and animation */
.image-container img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 20px;
  transition: opacity 1s ease-in-out;
}

/* Dot controls */
.dots {
  margin-top: 20px;
}

.dot {
  height: 12px;
  width: 12px;
  margin: 0 5px;
  background-color: #bbb;
  border-radius: 50%;
  display: inline-block;
  cursor: pointer;
  transition: background-color 0.3s;
}

.dot.active {
  background-color: white;
}

.fade {
  animation: fadeEffect 1s ease-in-out;
}

@keyframes fadeEffect {
  from {
    opacity: 0.5;
  }
  to {
    opacity: 1;
  }
}

/* Remove unwanted scroll bars or padding */
body, html {
  margin: 0;
  padding: 0;
  overflow: hidden;
}
```

## OUTPUT
<img width="1919" height="1199" alt="567392290-70628f03-0483-4529-bc76-b912e3e0ff4b" src="https://github.com/user-attachments/assets/f65621ed-3755-4809-bb7a-2edcb3de43ef" />

<img width="1919" height="1199" alt="567392297-face3643-0ac5-4be4-a9c0-20187b0e2984" src="https://github.com/user-attachments/assets/5a1236d0-7052-4489-a7f2-b43587e797c9" />

<img width="1919" height="1199" alt="567392308-9b8a31f6-6407-477b-90de-8272d2590ba2" src="https://github.com/user-attachments/assets/b435c50f-9591-4391-ae03-a8274c4e7843" />


## RESULT
The program for creating Image Carousel using React is executed successfully.
