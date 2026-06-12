---
title: "Too many entries in GRUB"
date: 2011-04-08
forum: Installation &amp; Upgrades
---

### Post by telovin on 2011-04-08
Hi,
I have so many entries in GRUB and have to actually scroll down so much to see windows entry. How do I remove unwanted entries in GRUB? Also How can I make a background picture appear when grub manager comes up?Kindly help.

---

### Post by Enigmapond on 2011-04-08
I use Ubuntu-Tweak for that. Among some really great functions, it has a Kernel Purge function in the package cleaner section. I recommend this. Open terminal and do:

```
[FONT=monospace]sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update && sudo apt-get install ubuntu-tweak
```
[/FONT][COLOR=#FFFFFF]
[/COLOR]

---

### Post by Dutch70 on 2011-04-08
Just so you know, it's a good idea to keep at least 2 kernels in case of problems with one of them.

To add pictures, try installing Grub Customizer from synaptic package manager, it may be in software center too, not sure. 

If you don't want to remove them with Ubuntu Tweak, open synaptic and search for "image-2" and remove any kernels you don't want. Careful not to remove the wrong one.

---

### Post by grahammechanical on 2011-04-08
Grub customizer is in the Ubuntu software Centre. You will need to search for grub-customizer. Otherwise you may not find it. You can also install some splash images. Search for grub-splashimages. They get put in usr/share/images/grub. You need to know the location so that you can use Grub Customizer to browse to the image file you want.

I recommend Grub Customizer. If you install more than one version of Ubuntu, as I have, and the new installation overwrites the Grub boot loader so that you no longer have the splash screen, as this recently happened to me, then Grub customizer has an option to install Grub in the MBR. And once again you will be using the Grub from your main Ubuntu.

Regards.

---

### Post by telovin on 2011-04-10
Hi,
When I open grub customizer, I am getting the following error messages.
"grub-mkconfig couldn't be executed. You must run this as root"
I try to right click to look for an option to run as root, but no. What is the command to run this as root?
(I have actually used grub customizer before,but now when I try to use it I am getting the above error message. I forgot how I used it with admin privileges)

---

### Post by Dutch70 on 2011-04-10
Hopefully you can find something in here to help.
If not, drs305 does answer questions in there also. 
[[COLOR="Red"]HOWTO: Grub Customizer [/COLOR]]("http://ubuntuforums.org/showthread.php?t=1664134")

---

### Post by telovin on 2011-04-10
I used ubuntu tweak,deleted some entries, but was showing error

```
"E: linux-image-2.6.31-20-generic: subprocess installed post-removal script returned error exit status 1
E: linux-image-2.6.32-23-generic: subprocess installed post-removal script returned error exit status 1"
```

I could delete some entries from tweak and in ubuntu tweak its showing only four entries now. I did sudo update-grub. Got the following error when I tried updating grub.

```
Generating grub.cfg ...
cat: /boot/grub/video.lst: No such file or directory
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found linux image: /boot/vmlinuz-2.6.32-27-generic
Found initrd image: /boot/initrd.img-2.6.32-27-generic
Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic
Found Windows 7 (loader) on /dev/sda1
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
/etc/grub.d/40_custom: 1: menuentry: not found
/etc/grub.d/40_custom: 2: Syntax error: "(" unexpected
```

Restarted the system. But my grub manager was still showing too many entries. It looks as if nothing got deleted. I tried to apply a back ground image, even that did not come.

I'll try grub customizer now.

I tried via synaptic, even synaptic showed the same errors.

---

### Post by telovin on 2011-04-10
I cant do anything with grub customizer. When I open it, it gives the following error
I open GC, it asks for password, I enter my admin password, it runs and again shows me the error message.
When I type sudo gksu grub-customizer from terminal then also I get the following error.

```
"grub-mkconfig couldn't be executed successfully. You must run this as root!
```
Thought "sudo' is for running as root.

I also tried the follwoing commands on terminal

```
sudo cp -R /etc/grub.d/ /root/Desktop
sudo apt-get update (I couldn't install it, it was showing errors.)
sudo apt-get purge grub-common 
sudo apt-get install grub-pc
```

When I typed sudo apt-get purge grub-common, I got the following errors.
```
(Got error messages:dpkg: error processing linux-image-2.6.32-27-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.31-20-generic
 linux-image-2.6.32-23-generic
 linux-image-2.6.32-26-generic
 linux-image-2.6.32-27-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


When I type the last command "sudo apt-get install grub-pc"

I get the following errors. I am copy pasting only the error part from my terminal.The whole thing is too long.

```
/etc/grub.d/40_custom: 1: menuentry: not found
/etc/grub.d/40_custom: 2: Syntax error: "(" unexpected
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.32-27-generic.postrm line 321.
dpkg: error processing linux-image-2.6.32-27-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.31-20-generic
 linux-image-2.6.32-23-generic
 linux-image-2.6.32-26-generic
 linux-image-2.6.32-27-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


I have 10-12 (or more don't know exactly) entries on grub. It is my parents who use this pc, so I want to make it simpler for them before I go. Kindly help.

---

### Post by oldos2er on 2011-04-10
Why not use Synaptic or apt-get to remove kernels you don't need? In Synaptic, search for "linux-image" and mark the ones you don't want for removal.

---

### Post by Dutch70 on 2011-04-10
> **oldos2er said:**
> Why not use Synaptic or apt-get to remove kernels you don't need? In Synaptic, search for "linux-image" and mark the ones you don't want for removal.

That was recommended in post-#3, see post-#7. Synaptic is giving errors. This is a whole new problem. Maybe it would be a good idea to start a new thread on that, if you can't find an answer via google or the search bar in this forum.

---

### Post by telovin on 2011-04-11
I tried synaptic and it showed the same errors. I have written it in the above post odsolo.Please read my post completely.
God I thought this thread was for customizing my grub and again why to start a new thread for the same problem? 
I also thought for problems related to Ubuntu I should come here and not google :(
All these things started after I changed my mother board and processor, and sometimes my ubuntu shows I dont have a genuine ubuntu which is not true. I downlaoded ubuntu when I had win xp But now I am using win 7. Do I need to activate Ubuntu with my new mother board and processor just like windows?

---

### Post by Dutch70 on 2011-04-11
> **telovin said:**
> I tried synaptic and it showed the same errors. I have written it in the above post odsolo.Please read my post completely.
God I thought this thread was for customizing my grub and again why to start a new thread for the same problem? 
I also thought for problems related to Ubuntu I should come here and not google :(
My Ubuntu has lots of problems after I changed my mother board and processor. It shows broken software packages and so many other things. But right now I am concerned about only tweaking the entries in grub.

You've been advised more than once on how to remove the entries, if synaptic is giving you errors, I doubt I'd consider that the same problem.

> I also thought for problems related to Ubuntu I should come here and not google :(
[[COLOR="Red"]http://www.catb.org/~esr/faqs/smart-questions.html#before[/COLOR]]("http://www.catb.org/~esr/faqs/smart-questions.html#before")
[[COLOR="Red"]http://www.catb.org/~esr/faqs/smart-questions.html#answers[/COLOR]]("http://www.catb.org/~esr/faqs/smart-questions.html#answers")

Also, if these problems are related to 11.04 which isn't even finished yet, they shouldn't even be in the support area of the forum. 
Good luck

---

### Post by telovin on 2011-04-11
Ohh k, Thanks Dutch, I'll try my luck with google.
Thanks a lot for your guidance!
Also I'll wait for someone else'e second opinions about grub before closing this thread as my problem is not solved.. Mean while I'll try google as per your suggestion.(I have followed everyones replies and also tried so many other threads about Grub2 on my own, None of them are working.)

---

### Post by Dutch70 on 2011-04-11
I really don't understand what you're trying to do. 

My understanding is this...
1. You're trying to remove old kernel entries from grub.
2. You can't because you're getting errors when you use synaptic. 
3. Instead of fixing synaptic, you want to find a different way to get rid of the old entries.

Is that correct? Or what am I missing???

---

### Post by telovin on 2011-04-11
Hi Dutch,
As per your advise, I will open a new thread for my synaptic errors. I have actually tried different ways to edit grub, one of them was through synaptic package manager.
The ways through which I tried to remove my grub entries were 

1.Terminal commands listed in grub 2 forums
2. Ubuntu tweak (I was able to delete some entries from Ubuntu tweak but some showed errors)
3.Synaptic package manager(Which showed the same errors as Ubuntu tweak. Error message is in my previous post.) and 
4.grub customizer.

I did "sudo update-grub" after Ubuntu tweak but the changes are not seen on my grub when I start up. It still shows 18 entries.Now I am trying to open the grub customizer. 
I had worked with grub customizer before, but nowadays when I try to launch it, getting error "you must run this as root". I managed to get past that error message by typing the command sudo grub-mkconfig. It just listed the entries on terminal did not launch GC.
If by any means I can launch the GC window, I guess I would be able to edit entries smoothly.

---

### Post by telovin on 2011-04-11
Hey Dutch 70,
Thanks a lot for your correct guidance. Hopefully when my synaptic issue gets resolved, I think everything will get resolved.:)

---

### Post by oldos2er on 2011-04-11
To run grub customizer, try **gksu grub-customizer**

---

### Post by telovin on 2011-04-16
I have done that. But was unable to. I could launch grub by typing gksu grub-mkconfig and it opens up and goes off. I tried to reinstall grub. After unistallation, I am unable to install it now.

---

### Post by telovin on 2011-04-16
I installed grub customizer. But still, I was unable to launch customizer. Thought it was a bug and resolved it with the developer. Now I am able to launch grub customizer with the command ```
gksu grub-customizer
```  I am able to edit it and save it :) Thank You all for helping me out!

---

### Post by telovin on 2011-04-16
Enigma pond, Graham mechanical, esp.Dutch70 and Oldos2er - Thank You all for helping me out :)

---

### Post by Dutch70 on 2011-04-16
You're welcome! 

So have you got this "Solved"?

---

### Post by telovin on 2011-04-17
Yes Dutch70, Very much so. :)

---

### Post by Dutch70 on 2011-04-17
Great, glad to hear it. You've had quite a time with this one.

---

### Post by telovin on 2011-04-17
Some other guys also had the same problem. So reported in launch pad and they resolved it for me. :)

---

### Post by thecamelcoder on 2011-04-17
I know its solved but here is a step by step guide someone might find useful one day. 

[http://www.linux-geek.co.nz/2011/04/11/how-to-clean-up-the-new-ubuntu-grub2-boot-menu/](http://www.linux-geek.co.nz/2011/04/11/how-to-clean-up-the-new-ubuntu-grub2-boot-menu/)

---

### Post by telovin on 2011-04-18
Thanks for the info thecamelcoder.

---

