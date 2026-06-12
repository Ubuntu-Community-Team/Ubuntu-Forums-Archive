---
title: "Keyboard suddenly types Arabic in login for Jaunty"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by lizardbliz420 on 2009-03-30
I have no idea on this one.  I had installed 9.04 on my HP dv 6500 pavilion notebook very successfully until today.  I shut down my computer and now instead of English when I type in the log in box is comes up in Arabic .  I have no idea why.  I tried using a USB keyboard which didn't work but when I put in a live cd it types in English.  How can I fix it so that when I boot from a hard drive?

---

### Post by Therion on 2009-03-30
Start with System/Administration/Language Support, I suppose, and hope that fixes things!

---

### Post by Sarai the Geek on 2009-03-30
Since you're beta testing Jaunty, don't forget to report this bug!

---

### Post by lizardbliz420 on 2009-03-30
Yes except I can't log in to get to the system administration.

---

### Post by Sarai the Geek on 2009-03-30
> **lizardbliz420 said:**
> Yes except I can't log in to get to the system administration.

Yes, I just realized that and logged out myself to check out your options. I'm on intrepid here but there should be an option to change the language for your session- in my GDM theme it is right under the login box but it may be different for you. See if you can find it and switch it back to English.
[IMG]http://lh6.ggpht.com/_FJH0hYZmVtc/ScRcoFARRuI/AAAAAAAABv0/dZ-MCL-j8Co/screenshot1_thumb%5B1%5D.png?imgmax=800[/IMG]
Try pushing options and seeing what it says. Is all that junk in Arabic as well? That may pose a problem, if it is.

---

### Post by lizardbliz420 on 2009-03-30
I have changed it to English from the options language interface and it is unsuccessful.  Any other ideas?

---

### Post by lizardbliz420 on 2009-03-30
None of the words are in Arabic.  All of it is in English except what I type in my login box

---

### Post by Sarai the Geek on 2009-03-30
> **lizardbliz420 said:**
> None of the words are in Arabic.  All of it is in English except what I type in my login box

Sounds like a bizarre bug. Have you tried just typing in your username and password, ignoring the fact that they show up in Arabic? I know it's a stupid suggestion but that's all I got.

---

### Post by lizardbliz420 on 2009-03-30
I have tried to log in ignoring that its in Arabic... got nothing.  Is there a way to edit a config file off of the hd when I boot the live cd that sets the keyboard recognition?

---

### Post by wigglydiggly on 2009-03-30
I can confirm bug.  I had just installed 9.04 beta, update/upgrade, reboot and language changed to hebrew I believe (typed text goes right to left)  ended up reinstalling and holding off update till this is fixed.

---

### Post by Sarai the Geek on 2009-03-30
> **lizardbliz420 said:**
> I have tried to log in ignoring that its in Arabic... got nothing.  Is there a way to edit a config file off of the hd when I boot the live cd that sets the keyboard recognition?

I don't know- it seems unlikely since live cds operate in the RAM only. I'll do some research and see if I can dig something up.

---

### Post by Sarai the Geek on 2009-03-30
I was wrong- apparently you can access the hard drive. Try this:
> First locate the partition that is your root. Try
sudo fdisk -l
for that task.

Now, let's say your root partition is hda1, let's mount it:
sudo mount -t ext3 -o defaults /dev/hda1 <mountpoint>
where <mountpoint> is an empty directory of your choice.

Then you should be able to copy your files around. If you have your /home on a separate partition you have to mount that as well.(source: [http://ubuntuforums.org/archive/index.php/t-250165.html](http://ubuntuforums.org/archive/index.php/t-250165.html))

Now we just have to find the config file that sets the input language, which I believe I have. See if the solution in the first response fixes the bug.
[http://www.linuxquestions.org/questions/linux-newbie-8/cant-change-keyboard-layout-in-ubuntu-8.04-login-screen-637811/](http://www.linuxquestions.org/questions/linux-newbie-8/cant-change-keyboard-layout-in-ubuntu-8.04-login-screen-637811/)

---

### Post by lizardbliz420 on 2009-03-30
WOOOOOOTTTT!! that worked

Ok so I inserted a live cd

mounted the original partition(in my case hda1)
then i sudo gedited the /etc/default/console-setup file on hda1
This is what it read:
> # The following variables describe your keyboard and can have the same
# values as the XkbModel, XkbLayout, XkbVariant and XkbOptions options
# in /etc/X11/xorg.conf.
XKBMODEL="pc105"
XKBLAYOUT="af"
XKBVARIANT=""
XKBOPTIONS=""

Then I changed XKBLAYOUT="af" to XKBLAYOUT="us" which fixed the problem.

Now how do i report that as a bug?

---

### Post by Sarai the Geek on 2009-03-30
> **lizardbliz420 said:**
> WOOOOOOTTTT!! that worked

Now how do i report that as a bug?

Awesome!

You'll need to make an account with Launchpad, and then you can file a bug here:
[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

In your report, include the following things:
-Brief description of your computer (i.e. HP Pavillion Laptop, 32 bit etc)
-Detailed explanation of the problem
-Since you fixed it, explain how
-The excerpt of your config file showing it was set to arabic

And you should be good!

Oh, also, since you're not the only one who has had this problem, I'm putting a post in my blog about how to fix it, hope you don't mind. ;)

---

### Post by xtoudi on 2009-03-31
Guys!!!!
Just read - and always use SEARCH - ALWAYS!! A few days ago!!

[http://ubuntuforums.org/showthread.php?t=1108548&highlight=input](http://ubuntuforums.org/showthread.php?t=1108548&highlight=input)

---

### Post by lizardbliz420 on 2009-03-31
I did search for it but I was looking for keyboard recognition issue which didn't lead me to that post.

---

### Post by Sarai the Geek on 2009-03-31
> **xtoudi said:**
> Guys!!!!
Just read - and always use SEARCH - ALWAYS!! A few days ago!!

[http://ubuntuforums.org/showthread.php?t=1108548&highlight=input](http://ubuntuforums.org/showthread.php?t=1108548&highlight=input)

Meh. ;)

---

### Post by lunatic77 on 2009-04-07
I'm having this exact same problem. FWIW I'm running Ubuntu 9.04 in a VirtualBox VM on a Mac (OS X 10.5.6). Thanks in advance for any help.

---

### Post by Sarai the Geek on 2009-04-08
> **lunatic77 said:**
> I'm having this exact same problem. FWIW I'm running Ubuntu 9.04 in a VirtualBox VM on a Mac (OS X 10.5.6). Thanks in advance for any help.

Read the whole thread- the answer is in there. It's also in my blog, this post: [Jaunty Default Keyboard Bug]("http://saraithegeek.wordpress.com/2009/03/30/jaunty-default-keyboard-bug/").

---

### Post by jtniehof on 2009-04-08
It appears this still hasn't been reported in Launchpad, so I made a [bug report](https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/357971). Thanks for this thread...saved my bacon :)

---

