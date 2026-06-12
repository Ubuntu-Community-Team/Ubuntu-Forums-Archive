---
title: "System boot hangs at battery check after upgrade"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by Bas1234567 on 2011-04-28
Hello,

I've just upgraded to Natty. During the upgrade no errors showed. However, when I now boot ubuntu (either recovery mode or normal), the boot process hangs at:

'checking battery state'

I searched for similair problems in this forum, but the solutions in other posts(sudo apt-get update & upgrade etc.) did not help.

I'm not sure if it is related or important, but when it hangs, it also shows something like:

'starting automatic crash reporter  [fail]'
'not starting jetty'
'saned disabled'

(this is from the top of my head, I can't copy there of course, so it is probably not exactly like this, or in this order...)

What can I do to get my ubuntu boot again?

Regards,

Bas

---

### Post by mlehner on 2011-04-28
Same *exact* thing is happening here. Word for word. Just a minor interruption to my work day. =(

The Battery check actually completes okay I think. It's whatever's after that that is hanging. Battery check is the last thing that shows up though.

---

### Post by aabler on 2011-04-28
I'm running Ubuntu as a VM (Parallels on Mac) and after the upgrade from 10.10 to 11.04, my system hangs during purple Ubuntu splash screen - it fills in the four "dots" and hangs forever.  Sounds like it may be a similar problem?  

I'll post as I troubleshoot if everyone else does the same we might converge on the right solution faster.

Prologue: Problem was with Parallels Tools.  Booted into terminal, changed the video adapter to vesa instead of the Parallels Video, removed the mount of the shared folders from fstab and things booted fine.

---

### Post by mlehner on 2011-04-28
The same thing happened here but if you hit Esc before it froze you can see where it stopped.

---

### Post by mlehner on 2011-04-28
I think this post just worked for me

The first solution (with a couple minor edits) helped get at least to the login screen before it locks up

[http://ubuntuforums.org/showthread.php?t=965180](http://ubuntuforums.org/showthread.php?t=965180)

Edit: Now it locks up right after logging in. I can move the cursor around but that's about it.

FYI: I don't know about everyone else but I am using an Nvidia card

---

### Post by Bas1234567 on 2011-04-28
I ended up doing a complete reinstall of ubuntu. Time-consuming, but at least it works again. Now I just have to find out how to get rid of the annoying unity-thing and get gnome back again....

---

### Post by mlehner on 2011-04-28
Did you do a fresh install of 11.04 or did you just stick with 10.10?

---

### Post by Bas1234567 on 2011-04-28
I still gave 11.04 an other chance, and so far, it seems to be OK. The problem of changing the interface back is one I can handle :)

---

### Post by Hedgehog1 on 2011-04-28
For those posters you might not know, you can load Natty/11.04 and still use the 'Classic’ UI: [**_Natty Info: Your UI options_**]("http://ubuntuforums.org/showthread.php?t=1741293")


***The Hedge***

:KS

---

### Post by mlehner on 2011-04-29
Yup reinstall worked fine...what a pain...

After playing around with the nvidia drivers I managed to controllably reproduce my second issue. If I used nvidia-current(270.x right now) then it broke. Unity would freeze immediately after logging in. So here's what I did to fix that.

1) The computer was working just Unity froze so I switched to another terminal (Ctrl-Alt-F5, GUI usually runs on TTY7[Ctrl-Alt-F7) and login
2) Run this(I purged and did a fresh install of the drivers)
```

sudo apt-get update
sudo apt-get purge nvidia-current nvidia-173
sudo apt-get install nvidia-173
sudo reboot

```

NOTE: I would still have to do
> The first solution (with a couple minor edits) helped get at least to the login screen before it locks up

[http://ubuntuforums.org/showthread.php?t=965180](http://ubuntuforums.org/showthread.php?t=965180)

to get past the Checking Battery State issue. I think there was a combination of two issues in my case.

---

### Post by Neovos on 2011-05-16
> **mlehner said:**
> Yup reinstall worked fine...what a pain...

After playing around with the nvidia drivers I managed to controllably reproduce my second issue. If I used nvidia-current(270.x right now) then it broke. Unity would freeze immediately after logging in. So here's what I did to fix that.

1) The computer was working just Unity froze so I switched to another terminal (Ctrl-Alt-F5, GUI usually runs on TTY7[Ctrl-Alt-F7) and login
2) Run this(I purged and did a fresh install of the drivers)
```

sudo apt-get update
sudo apt-get purge nvidia-current nvidia-173
sudo apt-get install nvidia-173
sudo reboot

```

NOTE: I would still have to do

to get past the Checking Battery State issue. I think there was a combination of two issues in my case.

I can confirm this was the same thing I did. I installed the nvidia-current drivers because, frankly, who's ever satisfied with slightly older drivers that are proven to work just fine?

I too was then stuck in the "checking battery state" spot. Since I had nvidia-173 drivers previously installed as well, your instructions above fixed my problem.

---

### Post by krsumani on 2011-05-22
Please refer to the following for the fixing the Battery check issue. It's fixed fine..
 
[http://vikashazrati.wordpress.com/2011/05/14/ubuntu-11-04-freezes-on-startup/](http://vikashazrati.wordpress.com/2011/05/14/ubuntu-11-04-freezes-on-startup/)

---

### Post by bmullan on 2011-08-01
I just had this "stuck on boot after battery check" problem occur on my system.

I have an ATI video card.

I tried some of the remedies posted here.

Disabled the ATI proprietary driver... didn't fix it.

Reinstalled the driver & activated it... didn't fix it.

Then I remembered I'd recently installed the upcoming 11.10 releases now lightdm manager.   I uninstalled that and now everything is back to normal.

---

### Post by FrankT-Qc on 2011-09-29
Just a note : 

I had the same problem (laptop would not boot on battery and stalled for a few minutes at battery check on AC).

I upgraded to 2.6.38-11-generic on a clean install without any of the fixes suggested on the net and the problem seams to be gone (still a little slow, but boots on battery)

---

### Post by zgembo on 2011-10-05
> **krsumani said:**
> Please refer to the following for the fixing the Battery check issue. It's fixed fine..
 
[http://vikashazrati.wordpress.com/2011/05/14/ubuntu-11-04-freezes-on-startup/](http://vikashazrati.wordpress.com/2011/05/14/ubuntu-11-04-freezes-on-startup/)

Thanks, it works for me, very nice and easy.

---

### Post by kooldino on 2011-10-15
[QUOTE=mlehner]
```

sudo apt-get update
sudo apt-get purge nvidia-current nvidia-173
sudo apt-get install nvidia-173
sudo reboot

```
[/QUOTE]

This worked for me.  Thank you!

---

### Post by lawrencrj on 2011-12-25
I am not looking for help but just thought that my situation might give some clue as to what is going on for the gurus on here.  The fact that my initial boot had no boot hand problem but just subsequent boots might mean something to a guru.  

I am a newbie to Linux -- someone told me that Ubuntu is the best way to start and that you can just set you BIOS to boot from USB and then download the most recent version of Ubuntu and use Universal USB installer with the ISO you have downloaded and put it on a flash drive.  So I did that, and after doing it Ubuntu booted with no problem ON THE FIRST TRY (!), but I could not get on-line because Firefox gave a message "can't load Firefox profile blah blah" so I pulled out the USB and booted to Windows XP and downloaded Chrome for Linux and saved it to where I could get at it once I was back in Ubuntu.   

However, when reinserted the USB flash drive and did a restart, Ubuntu hangs with "Stopping System V runlevel compatibility" and I tried several times and got the same result.   

It is odd because I made no changes (that I am aware of) while Ubuntu was running on the initial boot -- except that I put in my passphrase for my home network and got connected to the internet.

I am tempted to load the ISO to a CD where no changes CAN be made and see if it will boot twice or will just boot initially.   It makes no sense that it booted fine on the initial boot, but then will not boot again.   I will try the alt ctrl f1 and sudo startx (whatever the heck that is) and see if that helps MY situation.   (My situation is different that other posters on this forum in that I am not upgrading as the rest of the posters are, but rather just installing Ubuntu for the first time from the most recent version.   It is also different in that I had no boot error on the initial try whereas others could not boot at all after their upgrade.)  

If the startx does not work for me I will experiment with CD and then will look for an older version of Ubuntu that is not associated with this boot hang to use with USB.   Before CD I may reformat the flash and start over with the universal installer, but this time I will not reserve any room for saving nor try to open Firefox nor enter my passphrase and then see if it will boot on a second try.   I will report the results of my experiments if they appear to be helpful.

---

