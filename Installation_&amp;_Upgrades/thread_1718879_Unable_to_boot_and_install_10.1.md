---
title: "Unable to boot and install 10.1"
date: 2011-04-01
forum: Installation &amp; Upgrades
---

### Post by Jeyaprakash on 2011-04-01
I downloaded the ISO image of Ubuntu 10.10.. When I tried to boot, it gives an error message 'GLib Warning **: getpwuid_r(): failed due to unknown user id (0)' 

When I searched in the forum, I learn that the only possible way is to download some mini version of ISO and completely install being connected to the internet. It is strange that the iso has not been updated even after finding the problem. Also, there was no warning on the main download page regarding this issue. My whole download is a waste of time? Is there a way to install without any fresh download? Kindly help!!

---

### Post by Bucky Ball on 2011-04-01
Install 10.04 LTS instead. More stable, will help you learn the ropes, and longer support life. 10.10 is a rolling release which means problems are more likely to occur, particularly after updates. 

;)

---

### Post by Jeyaprakash on 2011-04-01
Hope it is better to go for only LTS versions. But, it would be annoying for anyone who downloads 10.1 when one comes to know that the whole download is a waste. In country like India, most of us have limited bandwidth at home. So if around 700 MB goes for waste, it is frustrating. There should be a warning that whoever wants to use 10.1 should directly install from internet by downloading mini iso and not through downloading the regular iso.

---

### Post by Bucky Ball on 2011-04-01
Not sure what this mini-iso is. The 10.10 regular ISO should be burned as an image to a CD then boot from that to try it out or install. Please explain this mini-iso and reference the thread that advises you to do it that way if you can. 

Never heard of it. Isn't necessary. ;)

---

### Post by plucky on 2011-04-01
> **Bucky Ball said:**
> Not sure what this mini-iso is. The 10.10 regular ISO should be burned as an image to a CD then boot from that to try it out or install. Please explain this mini-iso and reference the thread that advises you to do it that way if you can. 

Never heard of it. Isn't necessary. ;)

See [Here](https://help.ubuntu.com/community/Installation/MinimalCD)


@Jeyaprakash

Did you verify the download using [Howto Md5sum](https://help.ubuntu.com/community/HowToMD5SUM) before burning to Cd.

Then did you burn the .iso as an image? 

See [Howto Burn Iso](https://help.ubuntu.com/community/BurningIsoHowto)

Good Luck

If you already have a good copy of 10.10 then there shouldn't be any problem installing it.Just because some people have problems installing it doesn't mean you will also.

---

### Post by mörgæs on 2011-04-01
There is no need for checking the MD5 sum. If you get the error message, the CD is correct.

Here is an explanation:
[http://ubuntuforums.org/showthread.php?t=1443231](http://ubuntuforums.org/showthread.php?t=1443231)

You can jump to post 176, if you don't want to read it all :-) The mini.iso is explained here.

---

### Post by Jeyaprakash on 2011-04-01
Thanks for all the posts. Before posting here, I had read the following thread (post #176)

[http://ubuntuforums.org/showthread.php?t=1443231&page=18](http://ubuntuforums.org/showthread.php?t=1443231&page=18)

According to that, I have to download the mini.iso and depend on the internet for the entire download again. It would be better if the regular iso is fixed so that others who download the regular iso of 10.1 need not face this problem.

It is good that the problem has been solved in 10.04.2. In the same way, if the problem could be solved in 10.1, it would be great. 

Hope there is no other way left for me other than to download the entire thing again. I would go for 10.04.2.

---

### Post by Bucky Ball on 2011-04-01
> **Jeyaprakash said:**
>  I would go for 10.04.2.

I would, too, even though it might take awhile for you. You'll probably get a smoother ride and won't need to download a new version until April 2013.

---

### Post by Jeyaprakash on 2011-04-01
I have already started downloading 10.04.2. The internet connection is very bad today. Speed is only 30 kb/s. I have been downloading it for the past few hours. Hope it would take few more hours.

Hope the installation would be smooth.

I kindly request the Ubuntu team to leave a proper instruction on the download page (for installing 10.1, if anyone wants to) regarding the process to be followed using the mini iso. It would be better if the regular iso is fixed. 

I have been using ubuntu for the past few years. I wanted to download the latest version for my friend. If one thinks of giving a try to ubuntu and undergoes this process, it would be really passing a bad idea.

Hope everything is fixed soon.

---

### Post by mörgæs on 2011-04-01
I agree that it would be good to have a fixed 10.10 ISO, but they are never updated for the regular versions (only for long term support, where they come in four updates). 

By the way, the name is 10.10 and not 10.1. It refers to year and month of the release.

---

### Post by Jeyaprakash on 2011-04-01
@morgaes : Thanks for the correction and letting me know the finer information behind the version name.

If the 10.10 ISO is not going to be fixed, I don't understand the reason behind keeping it in the main download page, mentioning it the latest.

Everyone who downloads it would go through the same process. There is no way to install it though it boots, using the regular ISO.

---

### Post by mörgæs on 2011-04-01
> **Jeyaprakash said:**
> 
Everyone who downloads it would go through the same process. There is no way to install it though it boots, using the regular ISO.

Well, to be fair it works on most machines, else it would not have been released.  

Though, it would be an easy step with a great benefit to release a new ISO every month with all cumulated bugfixes. You can promote the idea here: 

brainstorm.ubuntu.com

---

### Post by Jeyaprakash on 2011-04-01
I successfully downloaded the 10.04.2. I happily burned the image on a CD and booted the system. I then got an error message

{initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.sqyashfs) on //filesystem.squashfs

I was really sad. I then searched the forums and came to know that this problem could be solved if booted from pendrive. That would be my last resort. Dont know what is happening to the Ubuntu these days.. The process is really getting hard.. 

Let me try and update the result in the forum. Already feeling drowsy!!

---

### Post by Jeyaprakash on 2011-04-01
Wah!! A great relief.. Finally installed Ubuntu 10.04.2 booting from the pendrive. Posting this message with the newly installed Ubuntu..

Success at last. Ha!!

---

