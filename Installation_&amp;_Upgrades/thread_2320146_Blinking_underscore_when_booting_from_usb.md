---
title: "Blinking underscore when booting from usb"
date: 2016-04-11
forum: Installation &amp; Upgrades
---

### Post by matko.mat on 2016-04-11
Hello, 
I first want to install Linux Fedora 23. I downloaded .iso file and i burn it to usb. I reboot my PC and I selected "boot from usb" in boot menu. It only show me the blinking _ in top left corner. I waited 5 minutes. Still blinking underscore...:( I think it is a fedora bug. I install ubuntu on my usb, reboot PC, "boot from usb" and BLINKING UNDERSCORE IN TOP LEFT CORNER AGAIN!!! ](*,). PLEASE HELP! WINDOWS IS BAD!

---

### Post by mörgæs on 2016-04-11
Please begin with a complete hardware description, especially of the graphics processor.

---

### Post by matko.mat on 2016-04-11
[LIST]
[*]                                                                                                  Graphics Processor                                                             
                                                                                                                                          Intel GMA 950                                                                                                 

[*]                                                                                                  CPU                                                             
                                                                                                                                           Intel Core 2 Duo T5500 / 1.66 GHz                                                                                                  

[*]                                                                                                  Number of Cores                                                             
                                                                                                                                          Dual-Core                                                                                                 

[*]                                                                                                  Cache                                                             
                                                                                                                                          L2 - 2 MB                                                                                                 

[*]                                                                                                  64-bit Computing                                                             
                                                                                                                                          Yes                                                                                                 

[*]                                                                                                  Data Bus Speed                                                             
                                                                                                                                          667 MHz                                                                                                 

[*]                                                                                                  Chipset Type                                                             
                                                                                                                                           Mobile Intel 945GM Express                                                                                                  

MEMORY
[LIST]
[*]                                                                                                  Size                                                             

                                                                                                                                          2 GB                                                                                                 

[*]                                                                                                  Technology                                                             
                                                                                                                                          DDR2 SDRAM                                                                                                 

[*]                                                                                                  Speed                                                             
                                                                                                                                          667 MHz                                                                                                 
[/LIST]

                          
[/LIST]

---

### Post by RobGoss on 2016-04-11
Hello and welcome to the forum.

This can happen for many reasons so it's hard to pin point what's causing this. 

You might want to read this post to see if it will help you.[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

---

### Post by matko.mat on 2016-04-11
I will check my iso with MD5, USB drive is 4 gb. The post did not help me because i haven´t got a live CD and installed linux now! In the post is no info about black screen with blinking underscore. 

P.S.
When I have the black screen, I tried to click all buttons on keyboard. NOTHINK

---

### Post by RobGoss on 2016-04-11
I've had problems like but after a few attempts  managed to it Ubuntu installed and every time this has happened it was on my older machines so I can't  be 100% sure what caused it. Try this post from the fourm.[http://ubuntuforums.org/showthread.php?t=1484694&page=3](http://ubuntuforums.org/showthread.php?t=1484694&page=3)

---

### Post by MAFoElffen on 2016-04-11
At the request of the OP via PM, here I am. Thank you for the invitation to assist. 

Lets back up [COLOR=#008000]*one*[/COLOR] step further. 

I saw "Chipset Type Mobile Intel 945GM Express," which implies this is a mobile device along the lines of a laptop, notebook or tablet.
- What make, model and category (laptop, notebook or tablet) is this device?
- Does it have legacy or uefi bios?

On the device that are preparing the Live image to your USB thumbdrive *from*:
- What is the OS of that machine?
- What is the program that you are using to make that image bootable on your USB device?

Other details... 
- What is the USB thumbrdrive make and model? (This sometimes does matter.)
- What is the image name that you are trying to boot?

Analysis: This is how I see this. The Op is trying to boot his Laptop(?) from a LiveUSB the he prepared and before even getting to the initial syslinux first screen, he only gets a flashing cursor... At that point in a device boot, before the syslinux decision point to boot graghically or to vga graphics/text console ... you need to confirm that the LiveUSB device is actually bootable.

His equipment, by spec's should boot a Live Image with Graphics... But I don't thinks he's even getting to that point in the decision tree yet. Meaning: It's broke. Confirm what is not wrong, before investigating what is wrong.

I will follow this thread and try to assist in finding a solution.

---

### Post by matko.mat on 2016-04-12
I write answers for your questions on paper and when I read qestion 4... I DON´T KNOW I NEED PROGRAM FOR CREATING BOOTABLE USB! I ONL EXTRACT IT TO USB WITH TOTAL COMMANDER!!! Ok, I try to create bootable usb with some program. I write here when I have some problem again! THANKS

---

### Post by matko.mat on 2016-04-12
Hello, Categorizing to: solved. I am writing from my ubuntu. I finnaly selected ubuntu, no fedora: ubuntu have bigger and better community, is more used, and... WHY FEDORA? :-> So thanks Mafoelffen.

---

### Post by MAFoElffen on 2016-04-12
You are very welcome. Any time. So ... Just to make sure (Because you say you are now working, and you marked this as "Solved"... So now do you have bootable LiveUSB, and you can install with no problems? (I just want to ensure you are taken care of before I stop following this thread.)

To explain the logic of those questions... If the laptop were Legacy bios, then there is a myriad of tutorials and instructions out there to take an iso image and create a bootable LiveUSB from a machine running Linux or Windows. Same if your Laptop were UEFI. If your Laptop is UEFI boot, then the LiveUSB needs to have an EFI boot file on it to boot...

I create my UEFI LiveUSB drives from Windows from a program called "Rufus." Free and easy to use. If I write them from a Linux box, then I use methods similar to this: 
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)

From your description, it sounds like you are using either, a derivative of, similar to or the Linux LiveUSB Creator toolset(?)

To others that see this later... Diagnostics flow. Look back to post #1 of my sticky (in my signature line) for that diagnostics flow chart. To boot Linux, there is a logical sequence of things that occur when booting Linux, whether from a LiveCD, LiveUSB or from a Bootable Hard Disk. I have a flow chart in that first post that would help point to where to look if you get or not get certain things in that sequence...

I saw that you were not getting a bootable USB drive. How? If it were bootable, then the first screen / panel you would see would be almost black ... rather more purplish, with an icon at the bottom... Even if a graphics issue, then you would get at least that panel first... (because that panel is just basic VGA graphics...) If it were graphics issue related, most graphics issues are after that initial panel. (But he has an "Intel" GPU, which is open source, so included with XServer...) There are more details to this, but I think it would muddy this thread...

---

