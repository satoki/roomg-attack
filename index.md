# Roomg-Attack
Privacy invasion attack that reconstruct real rooms through holes in virtual background.  

## What is Roomg-Attack?
Roomg-Attack is a privacy invasion attack that uses the instability of virtual background.
Recently, COVID-19 has required us to work from home.
The real background of the room is a treasure trove of information, the view outside the window identifies the location of our home, and the objects represent personality.
To protect our privacy we use virtual background.
This attack is an invasion of privacy by reconstructing the real background through the cracks in that virtual background.

## New attack surface
We found that the holes in virtual background contain at least one pixel of information about the real background.
The faster we move, the wider this hole gets, but no one in the world is paying attention.
**This is 0day of the real world.**

![img1](images/img1.png)  

We manually collected and pieced together the red circles in the image. Fortunately we have many frames.
The result was fabulous!
We were able to reconstruct a real background.

![img2](images/img2.png)  

The problem with this attack is that it is very time consuming, but it shows that an attacker can extract real room information if he takes the time.

## Automation algorithm
First, the ideal video is used.
In the ideal video, the virtual background is red, the real background is light blue, and the human is yellow.
After that, it is applied to the actual video.

![img3](images/img3.gif)  

The basic idea is to reconstruct the room by trusting that virtual background immediately hides the real background and choosing a color with a short appearance time for each pixel.
The following images are enlarged and arranged in the same section of the ideal video.

![img4](images/img4.png)  

Looking at the color of a single pixel over time, the light blue virtual background appears the least.
The pseudo code to collect this is simple.

**[GitHub - satoki/roomg](https://github.com/satoki/roomg)**  

The ideal video can be reconstructed.

![img5](images/img5.png)  

As the number of frames and video length increase, the accuracy of the restoration improves.
The problem is when the colors of the virtual background and the room mix at the boundary.
This is eliminated by using the color difference between the virtual background and the room.
In the future, the color difference calculation may have a significant impact on improving accuracy.

Let's attack the actual video.
The red circle in the image has been reconstructed.

![img6](images/img6.png)  

Compare with the image without virtual background.

![img7](images/img7.png)  

The background has been reconstructed with considerable accuracy.
This may allow the attacker to save time and invade our privacy.

## Evaluation
**[The Technical Report](http://id.nii.ac.jp/1001/00209447/)** has more details.

## Author
Satoki Tsuji ([@satoki00](https://twitter.com/satoki00))  
Ryusei Ishikawa ([@ryusei_ishika](https://twitter.com/ryusei_ishika))  

## Timeline
**September 24, 2020** We discovered the idea of Roomg-Attack for the first time in the world (**[Link](https://qiita.com/satoki/items/2770a28fd319113ca31b)**)  
**October 03, 2020** We have published a proof of concept for Roomg-Attack (**[Link](https://github.com/satoki/roomg)**)  
**October 27, 2020** We have released python software (**[Link](https://pypi.org/project/zoomg/)**)  
**October 31, 2020** We presented Roomg-Attack at AVTOKYO (**[Link](https://www.avtokyo.org/2020/event#h.3xesf54ajoe3)**)  
**February 22, 2021** Our technical report has been published (**[Link](http://id.nii.ac.jp/1001/00209447/)**)  
**March 01, 2021** We presented Roomg-Attack at ICSS (**[Link](https://www.ieice.org/ken/paper/20210301ZCDg/eng/)**)  
**June 21, 2021** Our research won an award (**[Link](https://www.ieice.org/iss/icss/award.html#2020)**)  
**July 07, 2022** We published this page  
