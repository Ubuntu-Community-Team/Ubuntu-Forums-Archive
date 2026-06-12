---
title: "the symbol 'grub_puts_' not found"
date: 2010-02-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rtalcott on 2010-02-03
did a clean 64 bit install...all goes well...I reboot...I see:

GRUB loading
error: the symbol  'grub_puts_' not found

then I get a prompt:
grub rescue>

I had Lucid installed...I hosed it...tried to reinstall and this is what I am getting...any guidance would be appreciated...

Thank you,
rt

---

### Post by ubername on 2010-02-03
Do you have bootable installs on different drives (with different MBR's)? I had a similar problem. If so try disconnecting one of the drives (e.g. a USB drive) and see how you get on.

---

### Post by SevenMachines on 2010-02-03
i think this is one of those where a new version of grub is installed but the old version is still on the mbr. you need to reinstall the newer grub to the hard drive, and you'll need a livecd or a separately bootable partition to do it

---

### Post by rtalcott on 2010-02-03
Ahhhhhhhhh...yes...and actually...I was finally thinking about this too...I will disconnect the other drive...I hope it's this simple!

I appreciate the advice!
rt

---

### Post by rtalcott on 2010-02-03
Pulled the other drive...no cigar BUT I'll try a clean install.
rt

---

### Post by rtalcott on 2010-02-03
How do I remove the old grub and reinstall the new?  I have a usb to boot from...
thanx
rt

---

### Post by ubername on 2010-02-03
[http://manpages.ubuntu.com/manpages/lucid/en/man8/grub-install.8.html](http://manpages.ubuntu.com/manpages/lucid/en/man8/grub-install.8.html)

try messing with that - I can't remember exactly how I fixed it but I think this may help.

---

### Post by VMC on 2010-02-03
> **rtalcott said:**
> How do I remove the old grub and reinstall the new?  I have a usb to boot from...
thanx
rt

You mean you installed Ubuntu on a usb drive? Not sure I understand, but from a livecd use the terminal to output 'sudo fdisk -l' so we see what your trying to accomplish. Plud in all drives that you want to use.

---

### Post by rtalcott on 2010-02-03
Sorry about my lack of definition...

I used unetbootin to load the latest daily build and it boots fine.

From the booted usb (on another machine) I am trying to install to a 30 gig Maxtor:

/dev/sdb1  83 System
/dev/sdb2   5 Extended
/dev/sdb5  82 Swap

---

### Post by rtalcott on 2010-02-03
and I continue to get (post install to the hard drive):

GRUB loading
error: the symbol 'grub_puts_' not found

then I get a prompt:
grub rescue>

It has been suggested that I remove grub which is what I am trying to do.
rt

---

### Post by SevenMachines on 2010-02-04
you dont need to remove grub, just reinstall it to the mbr. see [this guide.]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")
theres also a guide on how to [recover from the grub rescue> prompt here]("http://ubuntuforums.org/showthread.php?t=1195275") (section 15) which might be worth a try first, though you might find rescue mode isnt working in this case

---

### Post by ubername on 2010-02-04
Maybe try re-installing grub-pc. The version in Lucid has just been upgraded and now asks where you would like grub to be installed. This may be true of other versions of Ubuntu. If you are not using Ubuntu for production stuff, maybe consider going to Lucid? (I have been using it since pre-alpha and it has been fine, but there will be plenty of chances for it to go wrong, however it is a tremendous learning experience!)

(Just realised you are booting from USB - does that upgrade the same way as a normal distro anyone?)

---

### Post by rtalcott on 2010-02-04
Thank You!  i will attempt this shortly!
An interesting note is that OpenSolaris 2010.02 (Alpha) installed and boots with no problem.
rt

---

### Post by Vanishing on 2010-02-04
> **rtalcott said:**
> did a clean 64 bit install...all goes well...I reboot...I see:

GRUB loading
error: the symbol  'grub_puts_' not found

then I get a prompt:
grub rescue>

I had Lucid installed...I hosed it...tried to reinstall and this is what I am getting...any guidance would be appreciated...

Thank you,
rt

Reboot into a ubuntu install cd, choose the option "rescue a broken system.", follow the instructions and when there is a step asking you to mount a drive, choose your linux install(the one which installed your grub), then choose reinstall grub, type in (hd0), enter, reboot. viola.

---

### Post by rtalcott on 2010-02-04
I actually had 2 disks with this problem...and after much incoherent trial and error I managed to get one to boot...upgraded...got the grub update which I had write to both disks that I had the problems on...they were master slave...and now they both boot...

I suppose the thing to be learned here is that I need to read/learn about grub so I am not as clueless th next time.

I appreciate all the suggestions and assistance!

I will mark this as solved although I cannot describe the solution.
rt

---

### Post by Herman on 2010-02-05
Your error message: 'grub_puts_' not found , sounds a little bit similar to one I had a few days ago,

but the error message I had was more like: " **error: the symbol 'grub_term_outputs_disabled not found'** " , so maybe mine was a different error, I'm not sure.

Anyway, I booted up from another GRUB and ran 'sudo dpkg-reconfigure grub-pc', and that fixed mine. 
```
sudo dpkg-reconfigure grub-pc
```

---

### Post by rtalcott on 2010-02-05
I am going to write that down...I need to start keeping a notebook and logging what I do...
rt

---

### Post by VMC on 2010-02-05
> **Herman said:**
> Your error message: 'grub_puts_' not found , sounds a little bit similar to one I had a few days ago,

but the error message I had was more like: " **error: the symbol 'grub_term_outputs_disabled not found'** " , so maybe mine was a different error, I'm not sure.

Anyway, I booted up from another GRUB and ran 'sudo dpkg-reconfigure grub-pc', and that fixed mine. 
```
sudo dpkg-reconfigure grub-pc
```

That's a great command. I've never seen it before.
Actually I executed it from my current system just to see the results. Uses the "Display" so you can populate it at will, then creates the update-grub at the end.

This is great for those that haven't a clue as to where there grub is. I then ran boot-info-script to see where things were.
...just as I left them.

---

### Post by Kevbert on 2010-02-05
> **Herman said:**
> Your error message: 'grub_puts_' not found , sounds a little bit similar to one I had a few days ago,

but the error message I had was more like: " **error: the symbol 'grub_term_outputs_disabled not found'** " , so maybe mine was a different error, I'm not sure.

Anyway, I booted up from another GRUB and ran 'sudo dpkg-reconfigure grub-pc', and that fixed mine. 
```
sudo dpkg-reconfigure grub-pc
```

Got the same error. As soon as I run the above code I get 
> The following Linux command line was extracted form /etc/default/grub or the 'kopt' parameter in GRUB Legacy's menu.lst. Please verify that it is correct, and modify it if necessary.
Linux command line:


But I've just updated Lucid and am using Grub2 (it's supposed to boot sda1)???

---

### Post by drs305 on 2010-02-05
> **Kevbert said:**
> Got the same error. As soon as I run the above code I get 

Just to clarify what happens when you run that command:

You will be shown what the current options are on the linux/kernel line such as "quiet splash", etc. Normally the user can just use the tab key to move to and highlight the "OK" then press ENTER.

The process will be repeated. Basically you are being asked what you want for options during a normal boot, and the options during single user (recovery) mode.

Next you will be asked which drive's MBR to install GRUB 2. Use the space bar to select a drive, UP/DN cursor to move between drives, and the tab key to highlight the "OK". Then press ENTER to execute. You can select more than one drive, but you *should* select at least one. It will continue without selecting at least one, but you will encounter failures if you don't (barring special boot situations with other bootloaders, etc).

---

### Post by VMC on 2010-02-05
> **drs305 said:**
> ...but you *should* select at least one. It will continue without selecting at least one, but you will encounter failures if you don't (barring special boot situations with other bootloaders, etc).

From what happened when I ran it, it selected sda as default. It appears you **had** to select at least one.

---

### Post by Kevbert on 2010-02-05
I've tried to select sda but when I reboot I just get the grub prompt. 
I've tried re-installing grub2 from drs305's thread on grub2 recovery using a live CD and using the set command. I get no errors when setting the boot partition and then the system partition (which is on a different hard disk). When I enter
```
grub> boot
```
I get
```
error: no loaded kernel
```

---

### Post by drs305 on 2010-02-05
> **VMC said:**
> From what happened when I ran it, it selected sda as default. It appears you **had** to select at least one.

This is a new format but may be limited to Grub [noparse]1.98[/noparse]. I've seen it on my Lucid install ([noparse]1.98[/noparse]) but am not sure if it has been incorporated into 1.97~beta (Karmic). 

If one *must* be selected this is a welcome improvement as I've seen numerous failures because users didn't understand they had to select a drive (or didn't know to use the spacebar to select one) before pressing ENTER.

---

### Post by VMC on 2010-02-05
> **drs305 said:**
> ... be selected this is a welcome improvement as I've seen numerous failures because users didn't understand they had to select a drive (or didn't know to use the spacebar to select one) before pressing ENTER.It does select my sda as default, but I found out you **can** deselect everything. Why you would want to do this I have no idea.

---

### Post by VMC on 2010-02-05
> **Kevbert said:**
> I've tried to select sda but when I reboot I just get the grub prompt. 
I've tried re-installing grub2 from drs305's thread on grub2 recovery using a live CD and using the set command. I get no errors when setting the boot partition and then the system partition (which is on a different hard disk). When I enter
```
grub> boot
```
I get
```
error: no loaded kernel
```

Run boot-info-script after you do that so we can see where everything is.

---

### Post by ranch hand on 2010-02-05
It says right there in the box for the mbr how to navigate in it.  Up/down, space bar and everything.  It is the same box you get when you do your updates in apt.

If you add ureadahead and/or plymouth to that command it straightens that stuff out at the same time.  Well it has helped me that last couple days with these recent upgrades on a couple of installs (not all but worth the try).

That is a handy command for any package that you have a need to get configured correctly.  As much as I screw up, I need it.

Another thing that is handy is to have a chroot script for your OS stored on the OS (I have it on the desktop but any file will work).  If you have to get in with your LiveCD you just boot, pick up that file, save it to the Live Session desktop and you are ready to rock.

---

### Post by VMC on 2010-02-05
> **ranch hand said:**
> ...Another thing that is handy is to have a chroot script for your OS stored on the OS (I have it on the desktop but any file will work).  If you have to get in with your LiveCD you just boot, pick up that file, save it to the Live Session desktop and you are ready to rock.

You don't even need to copy it, just run the command as is. Or do as Kansas does and run it as multiple commands on one line, as such:
```
sudo mount /dev/sdaX /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

---

### Post by ranch hand on 2010-02-05
I really like to have "pts" and "sys" and;
```

sudo cp /etc/resolv.conf /mnt/Mini-root/etc/resolve.conf

```
in there too so that I have full internet access too.   It is nice if you need to remove/purge parts of the grub system and re-install the buggers.

I do not have a good excuse for liking to copy the bugger over to the CD desktop.  I just like it that way.

---

### Post by Kevbert on 2010-02-06
In the end I re-installed Lucid as it couldn't find any of my kernels (I had four different *buntus installed). Everything is now booting fine, but it's mystifying  why none of the Grub2 fixes could resolve the problem (well that's Alpha software for you...).:p:p:p

---

### Post by bonfire89 on 2010-03-23
I had the same problem as the OP with Ubuntu Server 10.04 beta.

I solved it by booting the iso, and hitting the rescue system option, which then lead me to a list where I was able to select "reinstall grub"

I selected that, typed in the proper drive for my situation and voila! done! fixed!

:D

---

