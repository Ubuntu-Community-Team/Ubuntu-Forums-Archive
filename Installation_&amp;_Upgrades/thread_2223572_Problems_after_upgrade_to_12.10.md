---
title: "Problems after upgrade to 12.10"
date: 2014-05-11
forum: Installation &amp; Upgrades
---

### Post by lile001 on 2014-05-11
Just upgraded a computer from 12.04 LTS to 12.10.  (I know, a little late, but hey, it was LTS.)  Everything was working fine until this point.  

When I reboot, I see the video screen start up, I see a choice of operating systems, I see a purple screen, then the screen says "monitor going to sleep" and there is no activity after that.  Doesn't respond to mouse or keyboard input.  Screen is black.  

so, what are my options at this point?

---

### Post by QIII on 2014-05-11
Hello!

Did you have a proprietary video driver installed?

Honestly, you'd have been better off waiting until the first point release of 14.04 before upgrading.  12.04 is supported until April of 2017.

12.10 reaches end of life in 5 days.

13.04 has already passed EOL, so you can't upgrade to that.

13.10 reaches end of life in July.

---

### Post by lile001 on 2014-05-11
Not totally sure about the video driver - I think it is Nvidea and I have dual monitors.  

I was on the way to upgrading to the current version.  So much for that plan, I should have left well enough alone and waited for the next LTS version.  Oh well, the damage is done.  

Am I stuck with re-installing the current version of Ubuntu from a CD and starting from scratch?  

Is there a way to hack an old monitor onto this box and see anything to get it running?

---

### Post by QIII on 2014-05-11
14.04 is an LTS version.  However, it is not until the first point release that you can usually do a direct LTS to LTS upgrade -- which would have meant a single upgrade.

What's done is done, so I suppose there's nothing for it now.

I suspect your problem is due to upgrading without first uninstalling a proprietary driver for your GPU. That is one of the quickest ways to reach a significant emotional event when upgrading.

 I'm not familiar enough with NVIDIA products to give you sure advice, so I'll defer to another.

Be patient.  I'm sure someone will come along shortly to help.

Best wishes!

---

### Post by lile001 on 2014-05-11
If folks think it might be worth a try, I'll hork a video card and a monitor from another machine, hopefully that might change the game.  Is this worth an attempt?

---

### Post by lile001 on 2014-05-11
Well, we will take small wins where we can find them.  I plugged in a different keyboard and mouse, and plugged in a video card from another computer.  Now, I DO have a linux command line.  Not that I really know what to do with such a wonderful resource.  However, that gives me some hope.  Can someone help me find info on installing Nvidea video drivers from the Terminal?  Not something I ahve ever encountered before.

---

### Post by lile001 on 2014-05-11
Blundering forward, and having little idea what driver or where it might be, I stumble across this blindingly brilliant idea:  search for the driver.  Man I am telling ya, this guy is really smart sometimes.  However, pulling that off is another thing, since I haven't a clue what I am about here.  

sudo find / -name 'NVIDIA*' doesn't seem to be producing any results.  Perhaps I've got something wrong in that command.

---

### Post by lile001 on 2014-05-11
I get the idea NVIDIA is caps, because I am looking at a page for some random nvidia driver that says it is in all caps.  However, I do find some subdirectories by searching without caps. So we know which subdirectories contain nvidia stuff.   SOOOO, all you fine Ubuntu geniuses out there (Is the plural of genius geniui?), perhaps we can noodle out how to proceed.  For I have little knowledge but much hope.  In other word I am pretty well stuck right now.

A summary of symtpoms for those TL DRs in the audience:  Upgraded from 12.04 to 12.10, lost graphical interface, but now have command line interface.  Probably need to install some nvidia driver, which is probably on my machine.  I have never installed such a driver from the command line, so I am hoping someone can give me a few hints.  Nor do I know where I should look for such driver.  But I have some hints.

---

### Post by lile001 on 2014-05-11
Ha! if one blunders about long enough, more light comes around.  I just hope the light is not an oncoming train.  

I saw this in another thread:

$ lspci | grep -i nvidia
02:00.0 VGA compatible controller: nVidia Corporation G98 [Quadro NVS 295] (rev a1)
03:00.0 VGA compatible controller: nVidia Corporation G86 [Quadro NVS 290] (rev a1)

One of those is an older card Horked from another brainbox.  (HORK is a technical term for stolen) and one is the video card that we haven't talked pretty enough to.

---

### Post by lile001 on 2014-05-11
I also see on another thread the possibility of doing this:

sudo apt-get install nvidia-current

However, I am reluctant to try that without confirmation from someone that this is a safe thing to do.  Please let me know if you agree with that, or have a better idea.

---

### Post by Michael_Duchemin on 2014-05-12
I had a problem getting a Dell with an Nvidia 8600GT to work in 13.10.  I couldn't get the GUI to boot and this solved the problem.  You'll likely need to bring up a non-GUI session with CTRL+ALT+F1.

[http://ubuntuforums.org/showthread.php?t=2197861](http://ubuntuforums.org/showthread.php?t=2197861)

---

### Post by lile001 on 2014-05-12
Knowing I have a : nVidia Corporation G98 [Quadro NVS 295] allows ,me to download a driver for this from Nvidia.  However I am faced with another challenge - how to move it to the dead brainbox.  I copy the file onto a memory card, stick it in the drive of the dead computer, but can't read it there.  I think I need to mount it, or something but I don't know how that works.  This is super-basic stuff, surely someone can throw out a clue.

---

### Post by lile001 on 2014-05-12
After a long diversion I was able to get the (hopefully) correct driver from Nvidia, get it onto the dead box, and run it.  THis minute I see an error message "The Distributed pre-install script failed!  Continue installation anyway?  Answering yes I soldier on.

---

### Post by lile001 on 2014-05-12
"The Nouveau Kernel Driver is currently in use by your system.  This driver is incompatible with the NVIDIA driver and must be disabled before proceeding.  please consult the NVIDIA driver README (which I do not have) and your linux distribution's documentation for details on how to correctly disable the nouveau kernel driver."

Now we are getting somewhere.  I understand none of what was just said.

---

### Post by lile001 on 2014-05-12
This thread seems to cover the subject but all I can make out of it is two experts seem to be arguing as to whether one of them has done a good or a bad thing.  Reluctant to break things further by trying some of this stuff, which is mostly out of my league.  [http://askubuntu.com/questions/112302/how-do-i-disable-the-nouveau-kernel-driver](http://askubuntu.com/questions/112302/how-do-i-disable-the-nouveau-kernel-driver)

---

### Post by lile001 on 2014-05-12
I was able to attempt to reboot in "failsafe graphics mode" but this produced an error message of "No screens found".  As it was displayed on a scree, I beg to differ.

---

### Post by lile001 on 2014-05-12
Looking into suggestions in this thread  [http://askubuntu.com/questions/112302/how-do-i-disable-the-nouveau-kernel-driver](http://askubuntu.com/questions/112302/how-do-i-disable-the-nouveau-kernel-driver)

Did this, as it seemed harmless enough.  Got past the Nouveu Kernel crap:

Run sudoedit /etc/modprobe.d/nvidia-graphics-drivers.conf and fill it with this:

  # This file was installed by nvidia-current-updates
# Do not edit this file manually

blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96
blacklist nvidia-current
blacklist nvidia-173-updates
blacklist nvidia-96-updates
alias nvidia nvidia_current_updates
alias nouveau off
alias lbm-nouveau off


re-ran the Nvidia driver shell script.  Cross fingers and make blood sacrifice to local gods.

---

### Post by lile001 on 2014-05-12
No joy in mudville yet.  

I am able to get to a terminal prompt using recovery mode, but it seems some kind of x-server isn't doing what it is supposed to.  Hopefully, dear reader, you will know what that means.

---

### Post by lile001 on 2014-05-12
I am going to try removing this bumblebee crap as suggested here: 

[http://ubuntuforums.org/showthread.php?t=2197861](http://ubuntuforums.org/showthread.php?t=2197861)

did this:
sudo apt-get --purge remove bumblebee
sudo reboot
and this:
you also have to remove /etc/modprobe.d/bumblebee.conf

but no change.

---

### Post by lile001 on 2014-05-12
Well, I was able to find solutions on Ask Ubuntu.  

Here is the rest of my saga of woe and intrigue, resulting in a working graphical interface: 

[http://askubuntu.com/questions/464825/black-screen-after-upgrade-12-10-now-a-very-simple-question](http://askubuntu.com/questions/464825/black-screen-after-upgrade-12-10-now-a-very-simple-question)

and here is where I found the answers that worked. 

[http://askubuntu.com/questions/41681/blank-screen-after-installing-nvidia-restricted-driver](http://askubuntu.com/questions/41681/blank-screen-after-installing-nvidia-restricted-driver)

---

### Post by mörgæs on 2014-05-12
Now the thread counts 20 posts of which 17 are your own. 

Please stop the repeated posting. If you have additional info the preferred way is clicking 'edit post'.

---

### Post by lile001 on 2014-05-15
Morgaes, 

My deepest apologies if my attempts to communicate clearly haven't met your exacting standards.  If you have anything to add that is actually helpful, I will be forever in your debt.

---

### Post by Jonor on 2014-05-16
If you have backups and can still get hold of a 12.04 boot disk, get out of 12.10 and back to 12.04 now.
Come September, revise that to 14.04, not before if you have a business hingeing on it.

---

