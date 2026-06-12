---
title: "Can't install onto HP Pavillion DV6000 notebook"
date: 2012-05-11
forum: Installation &amp; Upgrades
---

### Post by Geezer60 on 2012-05-11
I first attempted to Upgrade to 12.04  32 bit from 11.10 from the upgrade manager.  It immediately told me to insert the 12.04 disk, which of course i didn't have since I was ugrading.  So I downloaded and created the disk.  Tried upgrading again.  This time it told me it couldn't down the necessary files.  So I figured I'd do a clean install.  After going through the entire process, I got the unbuntu screen but no menus, no unity, no way to do anything.  After several reboots with no change, I created a flash drive, had exactly the same results.  I just finished reinstalling 11.10 and all my data.  Not very impressive so far.  I see a lot of other problems with 12.04 in the forums so I have to assume that some of you have actually seen it run.  Lucky you.

---

### Post by jadtech on 2012-05-11
??? you tried to do the upgrade online from the upgrade manager and it asked you  to insert  the Cd   are talking about ubuntu ??? 

you are not describing  an online upgrade at all first its software manager not upgrade manager , when  a distro up grade is available a button shows up at the top when you click it  you have to type in your password then files start uploading from the server about 4,000 of them or so it seems any how  and then after  about 2 hours these files start to de package  install and configure then clean up takes about another hour and a half or more  there is no request for a cd or disk what so ever .. 

if you are luck if your power and internet connection holds out the whole  time  in the end it requests you reboot and  if all went well you see your newly upgraded OS ..

at least this is how every upgrade I have ever done and anyone else I have seen here  up till this point ..

the whole Idea of online updates and upgrades is no need for burning  the Image to DVD or boolable USB, I will sahy it is more thena good Idesa to have a known working live CD  for problems that can happen   ..

---

### Post by jadtech on 2012-05-11
i have 12.4 installed on this HP  no problem  popped the dvd I made in the drive booted it  manually partitioned  while in live boot and  clicked install button  from ther it booted to  desk top and been running  it since ..

---

### Post by Geezer60 on 2012-05-11
yes, you read it right.  It surprised me too.  As I wrote, I didn't have a 12.4 disk because I didn't expect i needed one.  Way too many very strange things happened with this.  And I've been using ubuntu and upgrading on various computers since 9.04.  Many strange things happened.  Makes me afraid to try it on my desktop now.

---

### Post by Geezer60 on 2012-05-11
Oh and also we're both wrong.  It's update manager, not upgrade or software manager.  :)

---

### Post by jadtech on 2012-05-11
as far as I am aware the upgrade dont ask for a disk not at all so what ever  that is  I have no Idea shrug ..

not sure how much memory that lap top has it could be to your advantage if it runs windows to get gparted and make a swap partition  to help out the Live cd boot ..

 its software updater  to be technical as I pull down the menu here to be sure  :)

any how I noticed that you made a point of 32bit 12.4 is what you have ,  I know thats an old HP then the one I have here I  brought home last weekend and installed ubuntu on  nearly out of the box..

if that is a 32 bit machine keep in mind  the processor has to support pae  as of this version if  the procesor is older  you may have to install lubuntu  I beleve  they say wil still work ,,

---

### Post by Saewulf on 2012-05-12
I had the same exact 12.04 problem on my Pavillion DV6000 but installing from a 64bit desktop ISO disk I had downloaded.  *From the initial post in the thread: "After going through the entire process, I got the unbuntu screen but no menus, no unity, no way to do anything.*"

I should note that I had been running 10.04 since April 2010 on an 80Gb SSD.  With user data files backed up I indicated to the installer on the ISO disk to use the entire 80Gb for a new install.  There was no indication that anything was wrong until I booted from the new 12.04 install and it seemed to several minutes to get to a desktop, which as the creater of this thread indicated, had nothing on it and not way to do anything.  I was surprised because 10.04 had been the most seamless installation I'd ever done.  I'm sure I've done something silly but right off hand I can't see it.

Any thoughts or suggestions would be greatly appreciated.

---

### Post by Geezer60 on 2012-05-16
I just started this to provide info.  Since this seems to be  a shoulder shrugger, I've reinstalled 11.10 and will stick with it for whatever life remains in this old laptop.  When I feel the need for adventure, I might try installing 12.4 on my desktop.  Thanks guys.

---

### Post by commandojay1 on 2012-07-15
I understand this has been marked as solved, but the solution seems to be to re-install everything. I just went from 11.04 to 12.04 with the same issue. Boots up and shows only the desktop background image and something like an invisible bar at the top. 
I'll keep searching, but just in case can someone point directly to an ongoing post that is dealing with this issue?

I have a DV6000, to be specific, a DV6104CA.

---

### Post by commandojay1 on 2012-07-15
Well I solved the issue, at least for me fairly quickly. Once the blank desktop is up, press CTRL-ALT-DEL to get the log off screen. There are other ways to get to the login screen which you can look up. Once the login screen is there, press the Ubuntu button above the password window. Make sure it is for your login and not for the guest user. Select Unity 2D instead of Unity. Then login. Everything works at that point and allows you to see if there is better drivers for your system.

---

