---
title: "Problems with 16.4 GPU driver compatibility"
date: 2017-01-13
forum: Installation &amp; Upgrades
---

### Post by mjjenkins on 2017-01-13
There are already a lot of posts regarding this issue, but each one doesn't seem to include all aspects of the trouble I'm having. I have a Compaq Presario CQ50 that had Windows 7 installed. Its hard drive had all the main system and Windows files stored in a 9.36gb partition with another partition that had over 100g of free space, but It acted as though the computer was out of memory, so I installed some software to try and expand that primary partition. What happened instead was the whole drive got wiped. I then decided to just try to go ahead and do a fresh install of Ubuntu. I made and ISO on a USB flash drive and the initial installation went smooth. After going through all the installation procedure and logging in, everything was going fine except for a very significant amount of screen flickering. I searched through the forums and found a number of threads on this issue, and then through the command terminal, I installed a different Nvidia driver, and after restart I ran into the login loop. Again, there were a lot of threads covering this topic, so I found one that suggested to run the "purge nvidia" code and install yet another driver. After this procedure, I logged in and everything looked great upon first inspection, but this time simple dashboard items like "settings" etc began to either lag or freeze. The power down menu will pop up periodically and eventually the whole screen will go totally glitched out requiring a hard power-down via the power button. Im a beginner, so I know I dont have the terminology down for this and I do apologize for such a long post, but I just want to make sure I describe this as thoroughly and concisely as possible. So, to sum up..... its a Compaq Presario CQ50 with a clean install of Ubuntu 16.4.... the problem lies with the gpu drivers (I believe) and there are three specific symptoms Im having that havent been addressed all together as far as Ive seen. The laptop with Ubuntu is not my primary machine, and Im posting here via my main computer which has Windows 10. I know you are going to want to see specific error codes and such, but I have no way to copy/paste them in here from this computer, so if you need that let me know and I will type them in via a reply. 

Thank you all for any help, and I want to say that this seems like a great community of people. Im really looking forward to learning this awesome OS.

---

### Post by efflandt on 2017-01-13
Which specific CQ50 model do you have (numbers/letters that come after the CQ50)? From a quick web search, some models have Intel cpu and graphics, and some have AMD cpu and 256 MB Nvidia GeForce 8200M G (which I am not familiar with). Looking on Nvidia's website, they recommend version 340 drivers (nvidia-340 package).

But if you have one with Intel cpu and graphics, there is no point installing Nvidia drivers.

Open a terminal window (Ctrl+Alt+T) and see whether the following (lspci begins with small L) finds your graphics and mentions Nvidia:```
lspci | grep VGA
```

If so you might try the following (**apt-get** has been shortened to **apt** in 16.04, but either works):```
sudo apt purge nvidia*
sudo apt update
sudo apt install nvidia-340
```then reboot and see if it works any better

---

### Post by mjjenkins on 2017-01-13
its a cq50-130, but Ive already tried those steps. Im pretty sure its the 340 that causes the login loop..... or its the nvidia legacy something or other. Either way, Ive tried both and one does the login loop and the other freezes everything. As of right now a window popped up with an option to upgrade to the newest version of Ubuntu. I had 16.4. It is running this operation smoothly as of now, so maybe this version has a fix for that issue. I was thinking that there was a huge chance that this computer has an integrated chip seeing as most ordinary laptops do. This is just a low-end office laptop, so I thought it was strange that it would have a dedicated GPU. Anyway, hopefully this upgrade operation doesnt freeze right in the middle of it. Thanks for your reply

---

### Post by mjjenkins on 2017-01-13
actually, I think that might be exactly what is up with this..... it does have an integrated chip. Now to proceed from there

---

### Post by Bucky Ball on 2017-01-14
Just a tip: You will get better support if you use paragraphs in your posts and descriptive titles for your threads. Many people will take one look at a 'wall of text' like your first post and simply move on. Good luck. :)

---

### Post by efflandt on 2017-01-15
The CQ50-130 ***ONLY*** has integrated Intel graphics (Intel Graphics Media Accelerator 4500MHD), so you should not even be trying to install Nvidia drivers, which would do nothing at best, or potentially result in problems when you do not have Nvidia graphics hardware.

So just do:```
sudo apt purge nvidia*
sudo apt autoremove
```

---

### Post by mjjenkins on 2017-01-16
I was mistaken about the model number......... its actually a CQ50-215nr. Sorry about that

---

### Post by mjjenkins on 2017-01-16
To update you all on my situation.... Ubuntu froze completely and was totally inoperable, so I chose to make a bootable flash drive with the latest version of Linux Mint. Right now everything is working okay except the screen flickering. I'm able to open and run apps, but it still flickers really bad. The only exception to that is when I run the ZSNES emulator, which runs perfectly with no flickering. That definitely seems like a clue..... I just can't figure out what it is.

---

