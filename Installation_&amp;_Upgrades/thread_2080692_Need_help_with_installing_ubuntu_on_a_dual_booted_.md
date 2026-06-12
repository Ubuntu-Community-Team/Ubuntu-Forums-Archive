---
title: "Need help with installing ubuntu on a dual booted computer"
date: 2012-11-04
forum: Installation &amp; Upgrades
---

### Post by kidgrave on 2012-11-04
First, I installed windows xp on my computer, and then I dual booted with ubuntu. However, I deleted some of my apache files, but because I can't seem to figure out how to fix the issue of having to have done that. I just think it would be easier to re-install ubuntu.

Ok so yeah I have windows xp and ubuntu installed. I would like to re-install ubuntu again; however, I would like to do so on my current ubuntu installation.

I hoped that I explained myself clearly. Someone please help. thanks

---

### Post by zvacet on 2012-11-04
If you want to reinstall on existing Ubuntu partition then when you reach partitioning stage choose that partition and install Ubuntu on it.

---

### Post by ibjsb4 on 2012-11-04
An alternate way is in post #4

[http://ubuntuforums.org/showthread.php?t=1998923](http://ubuntuforums.org/showthread.php?t=1998923)

If you are not comfortable working with partitions just post a screenshot of gparted.  It will look something like this:

[http://www.dedoimedo.com/computers/gparted.html#mozTocId463215](http://www.dedoimedo.com/computers/gparted.html#mozTocId463215)

---

### Post by kidgrave on 2012-11-04
> **zvacet said:**
> If you want to reinstall on existing Ubuntu partition then when you reach partitioning stage choose that partition and install Ubuntu on it.

So which option would I have to choose while loading up the installation gui?

---

### Post by kidgrave on 2012-11-04
> **ibjsb4 said:**
> An alternate way is in post #4

[http://ubuntuforums.org/showthread.php?t=1998923](http://ubuntuforums.org/showthread.php?t=1998923)

If you are not comfortable working with partitions just post a screenshot of gparted.  It will look something like this:

[http://www.dedoimedo.com/computers/gparted.html#mozTocId463215](http://www.dedoimedo.com/computers/gparted.html#mozTocId463215)

I am not that comfortable when it comes to working with partitions. I'd appreciate it if you can tell me what to do. I have windows xp installed on /dev/sda1 , so here is a screen shot. Let me know which partitions to delete. thanks.[IMG]http://i48.tinypic.com/dyug6w.jpg[/IMG]

---

### Post by ibjsb4 on 2012-11-04
Simply delete sda5 and sda6, then install ubuntu.  You will be given the option during the install to install to the largest free space and that's all that you have to do.  Do not format the free space, just delete sda5 & sda6.

Also windows will not boot until ubuntu is reinstalled.  So you must install ubuntu immediately after deleting 5 & 6.

If you need further information, please post back.  :)

[http://www.dedoimedo.com/computers/gparted.html#mozTocId309606](http://www.dedoimedo.com/computers/gparted.html#mozTocId309606)

---

### Post by kidgrave on 2012-11-04
> **ibjsb4 said:**
> Simply delete sda5 and sda6, then install ubuntu.  You will be given the option during the install to install to the largest free space and that's all that you have to do.  Do not format the free space, just delete sda5 & sda6.

Also windows will not boot until ubuntu is reinstalled.  So you must install ubuntu immediately after deleting 5 & 6.

If you need further information, please post back.  :)

[http://www.dedoimedo.com/computers/gparted.html#mozTocId309606](http://www.dedoimedo.com/computers/gparted.html#mozTocId309606)

Thanks so much for your help :)  From what I can remember, you get 3 options to select from. So I choose the first one? I am not sure, and that is because from what I can remember, I think that it said that installing only ubuntu would delete any other partition

---

### Post by kidgrave on 2012-11-05
> **ibjsb4 said:**
> Simply delete sda5 and sda6, then install ubuntu.  You will be given the option during the install to install to the largest free space and that's all that you have to do.  Do not format the free space, just delete sda5 & sda6.

Also windows will not boot until ubuntu is reinstalled.  So you must install ubuntu immediately after deleting 5 & 6.

If you need further information, please post back.  :)

[http://www.dedoimedo.com/computers/gparted.html#mozTocId309606](http://www.dedoimedo.com/computers/gparted.html#mozTocId309606)

So if I delete 5&6, do I then select the option that let's me dual boot? or how would the swap be re-created? that confuses me a bit. :confused:

---

### Post by ibjsb4 on 2012-11-05
> **kidgrave said:**
> Thanks so much for your help :)  From what I can remember, you get 3 options to select from. So I choose the first one? I am not sure, and that is because from what I can remember, I think that it said that installing only ubuntu would delete any other partition

You are right.  One option will be to use entire disk, but do not do that.  That option will delete XP.

You would not of seen the option to install to the free space because you did not have any free space when you first installed ubuntu.  Now when you get to that point, the install to free space option will be there because you have created the free space.

---

### Post by ibjsb4 on 2012-11-05
> **kidgrave said:**
> So if I delete 5&6, do I then select the option that let's me dual boot? or how would the swap be re-created? that confuses me a bit. :confused:

Yes you want to dual boot.  The swap will be automatically created by the installer.  You will not have to do anything.

---

### Post by kidgrave on 2012-11-05
> **ibjsb4 said:**
> You are right.  One option will be to use entire disk, but do not do that.  That option will delete XP.

You would not of seen the option to install to the free space because you did not have any free space when you first installed ubuntu.  Now when you get to that point, the install to free space option will be there because you have created the free space.

Oh ok, well that explains why I had not seen that option lol, so that left me a bit confused. Alrighty, just to make sure I do not mess up. Do I choose the option to install into free spacer, or the one that lets me dual boot???

---

### Post by kidgrave on 2012-11-05
Sorry if I ask too many questions. I had to re-edit my previous post.

---

### Post by ibjsb4 on 2012-11-05
Both  :)  First the dual boot option and then the next screen will be the free space option.

If memory serves me right.

You can back out of the install at that point if you feel something is wrong.  Once you have partition and started the install, it must go the course.

Im calling it a night, so I wish you luck.  Not that its needed :) and will take a look in the morning.

---

### Post by ibjsb4 on 2012-11-05
> **kidgrave said:**
> Sorry if I ask too many questions. I had to re-edit my previous post.

Better the questions now than when its too late  :)

---

### Post by kidgrave on 2012-11-05
I booted from the live cd. On gparted I tried deleting sda5 and sda6, but I get an error that says unable to delete /dev/sda5.  Please unmount any logical patterns having a number higher than 5.

---

### Post by rj7 on 2012-11-05
When you boot from live cd delete (format) sda 6 first i guess it ll be unallocated or free(something like that )after that. Set that as swap. Then format the sda5(your current ubuntu installation) to ext4.  
This should work.

---

### Post by kidgrave on 2012-11-05
Thank you everybody for your help. I really appreciate it :)

Somebody from another forum helped me solve this issue with an easier method. So I will be posting here the method that worked for me for anybody who in the future wants to use it as reference, just in case they face the same issue as me. 

Here are the instructions:

Step #1. Go to  [https://docs.google.com/open?id=0B3e0lL ... zVFNGpmd2s]("https://docs.google.com/open?id=0B3e0lLG3OdqEaWp6QzVFNGpmd2s")

Step #2 Follow the advanced method 'something else' shown here and edit sda5 to format as ext4 and mount as /

After you are done with Step #2, then proceed to install, and that is all that you have to do.

---

