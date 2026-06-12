---
title: "update to Natty, aborted update...now I can't boot (fs doesn't have /sbin/init)"
date: 2011-04-03
forum: Installation &amp; Upgrades
---

### Post by pdepedo on 2011-04-03
First of all, good day to everybody.

I've been running Ubuntu 10.04 and today I found about the new version (Natty), and I decided to give it a try.
I created a live USB, started it, got into the desktop, and then ran "Install Ubuntu 11.04". I clicked "Update" and it went on.  Unfortunately the update just stopped, and I had it sitting in the desktop for almost an hour and the bar wasn't moving. I don't remember if I clicked the "Cancel" button, I don't even remember if the update window had a "Cancel" button. Since I couldn't find any way to close it, I logged out and then logged back in. I tried installing again...and this time the "Update" option was gone!

I restarted but now I came across an error like this: 
"Target filesystem doesn't have requested /sbin/init/ "
And other errors talking about how it was not possible to mount /root/dev, /root/sys, /root/proc.

Any ideas? I went online and searched the error, but haven't found anything for this. And yes, effectively my old Linux partition doesn't have the /dev, /sys or /proc folders. I tried copying them from the Live USB but it have me a "Can't copy special file" error.

The question here is: Can I do anything to save my old system? I'd do a clean install, but my Internet connection is extremely slow, and it's gonna take days to download all the updates and all the programs I had. Not to mention setting all up again.

Any help will be appreciated.

---

### Post by Hedgehog1 on 2011-04-03
A quick 'don't install in-development releases unless you are an advanced user' speech.  *Well, lets just say we did, you know this by now.*

To get the beta to install, you will need to uncheck the 'download updates during install' and 'download 3rd party...' check boxes.  The install needs to come strictly from the CD/USB.

Once loaded, you can get the updates using package manager. 

You will have some bugs and issues as the code changes from day-to-day, from little annoying things to 'big show stoppers'.

Most folks (myself included) are testing Natty on a separate system so if something tragic happens our primary PC is still operational.  If this is you primary PC - you really should think about going back to your previous Ubuntu release.

***The Hedge***

:KS

---

### Post by pdepedo on 2011-04-03
So my only choice right now is to do a clean install of the Ubutu 10.10? I really don't want to lose all my programs and settings…is there no way to fix my problem?  Maybe there's something I just need to change on a file accessed in the boot sequence.

Thank you.

[IMG]http://i.imm.io/4Lo3.jpeg[/IMG]

---

### Post by Hedgehog1 on 2011-04-03
Please do this, and that will tell us where things really are on your computer right now.

Please boot off the LiveCD/LiveUSB, select TRY, and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.


Then we can get your rolling.  Did you install with a separate '/home' partition?

***The Hedge***

:KS

---

### Post by drs305 on 2011-04-03
Your files may or may not be intact, but just wait until you post the RESULTS.txt and don't perform any write operations to your hard drive until we can try to determine the state of your system.

While your system files may be trashed, it could simply be that Grub2 needs some help finding the correct ones.

---

### Post by Hedgehog1 on 2011-04-03
> **drs305 said:**
> Your files may or may not be intact, but just wait until you post the RESULTS.txt and don't perform any write operations to your hard drive until we can try to determine the state of your system.

Wow!  The legendary **drs305** has entered the same thread I am working on, too.  I am SOOO excited!!  I have read all you grub guides!  I would ask for your autograph, but Hedgehogs don't carry pens. Or paper.  Or even have pockets...


***The Hedge***

:KS 

Seriously - your grub guides are awesome!

---

### Post by drs305 on 2011-04-03
:oops:

---

