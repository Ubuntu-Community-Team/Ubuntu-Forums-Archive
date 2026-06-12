---
title: "Install won't allow input of user password"
date: 2005-08-14
forum: Installation &amp; Upgrades
---

### Post by sweeneysmsm on 2005-08-14
I downloaded Ubuntu 5.1 and created my install CD from the image. All went very well. I put in the owner name, added in the user name, BUT when it asked for a password the keys that I entered with the keyboard would not enter at all. I went Back to earlier sections of the install but every time I got to the password point nothing happened. I tried going ahead without a password but it would not accept that either.

Any ideas more than welcome...

Mary

---

### Post by jasmuz on 2005-08-14
Did you try using another keyboard?....it could be a keyboard lockup. If not, then your installer might be messed up. Did you verify the MD5SUM of the image before burning?

---

### Post by sweeneysmsm on 2005-08-14
Thank you for your reply.

I don't think it's the keyboard because I have tried the install on two laptops and exactly the same thing happens at the password point.

How would I verify the MD5SUM of the image before burning? I don't really know the meaning of the term. 

To get the image I went to someone who had a high speed connection and downloaded it to the CD. The CD of course would not work to install the image. It said it was Read Only. I then posted my what to do question and got a helpful reply. I copied the CD to my hard drive and then used Roxio to do a Record CD from Image. I set it to Test and Record. Then I took the CD and put it in the laptop and was going just fine until this snag.

Any ideas gratefully appreciated.

Mary

---

### Post by ultima2k on 2005-08-14
Just type your password...it's the same for me that you can't see any output, but it works anyway..

---

### Post by heimo on 2005-08-14
That's a hard problem to debug. Which keyboard layout are you using / selecting during install? You could try something else.

Checking md5sum is a way to verify that the image isn't corrupted. To do that, you use md5sum program and compare the output to value on MD5SUMS file in the same directory you downloaded the file from. 

MD5SUMS file:
[http://us.releases.ubuntu.com/releases/5.04/MD5SUMS]("http://us.releases.ubuntu.com/releases/5.04/MD5SUMS")

How to check md5:
[http://www.linuxiso.org/viewdoc.php/verifyiso.html]("http://www.linuxiso.org/viewdoc.php/verifyiso.html")

EDIT: Could it be that you just don't get the usual ******* stuff when typing the password? (as suggested above?) Hopefully.

---

### Post by Ptero-4 on 2005-08-14
[QUOTE=heimo]That's a hard problem to debug. Which keyboard layout are you using / selecting during install? You could try something else.

Checking md5sum is a way to verify that the image isn't corrupted. To do that, you use md5sum program and compare the output to value on MD5SUMS file in the same directory you downloaded the file from. 

MD5SUMS file:
[http://us.releases.ubuntu.com/releases/5.04/MD5SUMS]("http://us.releases.ubuntu.com/releases/5.04/MD5SUMS")

How to check md5:
[http://www.linuxiso.org/viewdoc.php/verifyiso.html]("http://www.linuxiso.org/viewdoc.php/verifyiso.html")

EDIT: Could it be that you just don't get the usual ******* stuff when typing the password? (as suggested above?) Hopefully.[/QUOTE]
 Also be aware that the md5sum program isn't available for Windows. It's available on OSX though.

---

### Post by heimo on 2005-08-14
[QUOTE=Ptero-4]Also be aware that the md5sum program isn't available for Windows. It's available on OSX though.[/QUOTE]

[http://www.openoffice.org/dev_docs/using_md5sums.html](http://www.openoffice.org/dev_docs/using_md5sums.html)
[http://www.md5summer.org/](http://www.md5summer.org/)

---

### Post by sweeneysmsm on 2005-08-14
Thank you for replying.

I looked at [http://www.md5summer.org/](http://www.md5summer.org/) and they seem to have the download for Windows XP which is the OS I am using to copy the image to the CD.

Regarding the keyboard - I am using the inbuilt keyboard on the Dell Latitude CPi so don't have much in the way of an alternative...

I have ordered the original CD's and so when they come, I can probably rescue myself. I was hoping that I could get these laptops up and running so that a couple of people could take them with them now.

I did use the Record and Test settings when I did the CD burn so thought that all would be well.  Not so...

Thanks for any help available.

Mary

---

### Post by sweeneysmsm on 2005-08-14
Thank you to all who replied and most especially to ultima2K who provided the solution. It is true...you have to type in the password even though it does not appear to enter at all.

Mary

---

### Post by transactionlogfiller on 2005-08-14
This is something that confuses a lot of Linux newbies and tbh, I thought they had made it echo stars in the Ubuntu install. Perhaps that is just in Breezy.

I think the idea is that someone looking over your shoulder cannot even tell how many letters your password has, so it's even more secure than just starring it out.

---

