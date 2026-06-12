---
title: "upgrade from 11.10 to 12.04LTS hangs! Help!"
date: 2013-05-11
forum: Installation &amp; Upgrades
---

### Post by twgreg on 2013-05-11
Hi Folks,

Been running 11.10 for the past two years without any major problems (at least nothing that couldn't be solved with some google searching).  I have a laptop with dual-boot setup (Ubuntu / WinXP).  I recently decided to upgrade to 12.04LTS from the Update Manager.  

All went smoothly for about an hour then a terminal window appeared informing me that some true type fonts had to be installed (or something to that effect).  It wasn't a true terminal, it was a graphical display within the terminal (looked like an old MS-DOS screen). There was some text to read with an <OK> at the bottom of the screen.  It appeared to be prompting me for permission to proceed... but there was no way to respond to the window.  Nothing to select with the mouse... now way to select the <OK> with scroll keys or ENTER key... no way to respond, the installation was frozen.  I decided to wait for a while to see if it would proceed independently or present me with another prompt, but after an hour, still frozen.  I had no way to proceed with the install or to cancel.  I had to shut down and reboot.  That sent the computer into a black screen.

I was able to use a 12.04 iso on DVD to boot my computer and somehow, I found a way to get my computer back up with the recovery console and some terminal commands.  At this point, my computer boots up into 12.04, but it's an incomplete install and some features and programs no longer work.  Any attemps to finish the updates from Update Manager or from the terminal w/ "sudo apt-get install -f" are unsuccesful, the update still freezes or halts with error messages.

Is there a way to recover from this that doesn't require a degree in computer science (I am not a Linux geek... wish I was)?

Thanks for any advice you guys can offer.

Regards,
Tim

---

### Post by twgreg on 2013-05-11
replying to my own thread...

I just retried the update again from the terminal;

sudo apt-get update
sudo apt-get dist-upgrade

The computer doesn't lock up, but the installation freezes when it gets to the screen shown in the attachment.

How do I proceed from this prompt?  There doesn't appear to be any way to move forward from this.

Thanks,
Tim

---

### Post by ibjsb4 on 2013-05-11
> but there was no way to respond to the window.  Nothing to select with  the mouse... now way to select the <OK> with scroll keys or ENTER  key... no way to respond, the installation was frozen

Tab and Enter

---

### Post by twgreg on 2013-05-11
Thank you!!!  I'm obviously not much of a terminal user.  That did the trick.

---

### Post by Bucky Ball on 2013-05-11
@twgreg: I have attached your image and edited your post accordingly. You can mark your thread as solved (to help others) by editing first post, click 'Go Advanced' and change the prefix in the thread title to [SOLVED]. 

To all: Please refrain from inserting large images in the body of your posts. Thanks. ;)

---

### Post by ibjsb4 on 2013-05-11
And welcome to the forum :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

