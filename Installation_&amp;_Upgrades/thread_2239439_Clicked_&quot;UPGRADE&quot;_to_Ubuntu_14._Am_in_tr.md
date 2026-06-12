---
title: "Clicked &quot;UPGRADE&quot; to Ubuntu 14. Am in trouble!"
date: 2014-08-13
forum: Installation &amp; Upgrades
---

### Post by gabmuks on 2014-08-13
Hello and good day.

Update manager gave me an "UPGRADE" button to click on to upgrade to Ubuntu 14.

I trusted Update Manager so I clicked "UPGRADE".

The upgrade screen froze at "dpkg".

After waiting for two more hours, I told the computer to reboot.

I'm sure that was a mistake.

Have I lost everything stored on my computer?

Is there any way to salvage anything on there?

Thanks for your time.

Thanks for your time.

---

### Post by ubfan1 on 2014-08-13
I'm not aware of the Upgrade button ever causing data loss, but new kernels require new video drivers, which may need to be installed manually.  We'll need a little more information about your specific situation:
What were you running when you upgraded 12.04?
Any special disk setup like Logical Volumes or raid?
What video chip/driver were you using?
Did the computer reboot?  If not, what happened?
You should always be able to run a live media and look at your disk to confirm your files are still present.

---

### Post by kansasnoob on 2014-08-13
I've recently had upgrade tests take as long as 4 hours and I have a 12mbps connection.

Maybe try what I recommended here:

[http://ubuntuforums.org/showthread.php?t=2239290&p=13097139#post13097139](http://ubuntuforums.org/showthread.php?t=2239290&p=13097139#post13097139)

---

### Post by mastablasta on 2014-08-14
> **gabmuks said:**
> 

Have I lost everything stored on my computer?

Is there any way to salvage anything on there?



nothing was lost. system is damaged.

yes, you can save the system as well as data. if you do not want to save the system boot using liveCD/USB, copy the data and reinstall the OS.

if you have another computer someone on IRC channel could help you guide through the upgrade. you can restart it and it will re-download and rewrite  it all again and likely boot into workable OS. I had a similar thing happen to me only mine actually crashed during upgrade. so I removed all downloaded files and re-did the upgrade command. 

remounting systems could work and enable you to progress:
[http://askubuntu.com/questions/364605/fixing-failed-upgrade-to-13-10](http://askubuntu.com/questions/364605/fixing-failed-upgrade-to-13-10)[http://askubuntu.com/questions/364605/fixing-failed-upgrade-to-13-10](http://askubuntu.com/questions/364605/fixing-failed-upgrade-to-13-10)

still it would be good to know where the OS get's stuck on reboot. it all depends where the update got stuck.

---

### Post by gabmuks on 2014-08-14
Thanks to all for kind assistance!

Will try to give as much info. that my knowledge will allow.


First of all my original OS before Ubuntu 14 "UPGRADE" attempt
was Xubuntu 12.

I don't know if that is problem or not.

I do have an Xubuntu CD installation disk if that will help to salvage any of my saved files.

I booted up my computer from the installation CD and I see there is a "RESCUE MODE".

But I do not know how to use "Rescue" mode.

All that I wish to do is recover and copy my Document files from Xubuntu 12,
Then I will do a clean install of Ubuntu 14.


Would any of you be willing to walk me through the rescue process?

Thank you for your time.

---

### Post by gabmuks on 2014-08-14
Thank you for reply.

I was only running Xubuntu 12.04.

I have no knowledge of the Raid or other things metioned in your reply.
My computer is nothing special. Only used for email and pictures basically.

Only need to recover my document files if possible.
Right now Xubuntu will not boot up.
It gets as far as the words... "Xubuntu 12.04" with 4 dots below the words.

Then stops loading completely.

Thank you for your time.

---

### Post by gabmuks on 2014-08-14
> **kansasnoob said:**
> I've recently had upgrade tests take as long as 4 hours and I have a 12mbps connection.

Maybe try what I recommended here:

[http://ubuntuforums.org/showthread.php?t=2239290&p=13097139#post13097139](http://ubuntuforums.org/showthread.php?t=2239290&p=13097139#post13097139)

I would gladly try these commands that you have listed, but I am not  sure that I can even get to a "terminal" to enter the commands.

When I turn on this computer, it will only boot as far as the words "Xubuntu 12.04".

Then stops booting. Nothing happens after that. 				

But thanks for your help.

---

### Post by ubfan1 on 2014-08-14
At the four dots, type ESC (might have to try a few times) and you will switch over to a text screen with some error messages you can report here.  Then maybe we can figure out what's wrong.

---

### Post by kansasnoob on 2014-08-14
> When I turn on this computer, it will only boot as far as the words "Xubuntu 12.04".

Then stops booting. Nothing happens after that. 

Right, look there again:

[http://ubuntuforums.org/showthread.php?t=2239290&p=13097139#post13097139](http://ubuntuforums.org/showthread.php?t=2239290&p=13097139#post13097139)

> try entering a TTY using Ctrl+Alt+F1, then login as usual and try

Then try those commands, rinse-n-repeat as needed.

---

### Post by grahammechanical on 2014-08-14
It is not good to reboot part way though an upgrade to another version. You asked about Recovery mode. Select that and Linux will load and a menu will appear with these options.

resume - resume normal boot. That will/may load to the desktop will a fall back open source video driver.
clean - try to make free space.
dpkg - repair broken packages.
failsafeX - run in failsafe graphic mode.
fsck - check all files systems.
grub - update grub boot loader.
network - enable networking.
root - drop to root shell prompt.
system summary - prints out to the screen a system summary.

You could try selecting Network. That will establish a network connection. It will also put the file system into read/write mode which is necessary if you are going to add files to the file system.

Then when back at the recovery menu select Root. at the prompt you can try

```
apt-get update
apt-get upgrade
apt-get dist-upgrade
```

and see what effect those have. Make a note of any error messages.

this may restart the upgrade

```
do-release-upgrade
```

When finished type Exit to get back to the recovery menu and select Resume.

Regards.

---

### Post by gabmuks on 2014-08-14
> **ubfan1 said:**
> At the four dots, type ESC (might have to try a few times) and you will switch over to a text screen with some error messages you can report here.  Then maybe we can figure out what's wrong.

Thanks for reply

I typed in ESC after the 4 dots and then hit enter.

A cursor then appeared at the left side of the screen. (actually it was just a blinking _  I'm assuming that it might be a cursor.)


But no text appeared even after ESC and enter several times.

---

### Post by gabmuks on 2014-08-14
> **kansasnoob said:**
> Right, look there again:

[http://ubuntuforums.org/showthread.php?t=2239290&p=13097139#post13097139](http://ubuntuforums.org/showthread.php?t=2239290&p=13097139#post13097139)



Then try those commands, rinse-n-repeat as needed.

Cool!! Thanks!

I got the terminal per your instructions. Then I entered the first command you gave.

The message said:   dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.



I entered the command that the message gave. 
The command was excepted and alot of information started filling the screen.
The last line says:  gir1.2freedesktop


Should I do anything else at this point??

---

### Post by gabmuks on 2014-08-14
> **kansasnoob said:**
> Right, look there again:

[http://ubuntuforums.org/showthread.php?t=2239290&p=13097139#post13097139](http://ubuntuforums.org/showthread.php?t=2239290&p=13097139#post13097139)



Then try those commands, rinse-n-repeat as needed.

I typed into the terminal the second command you gave....
sudo apt-get -f installInformation again filled the screen. After about 5 minutes, the information stopped.

This is the last line in the terminal:


update-initramfs: Generating /boot/initrd.img-3.2.0-67-generic

---

### Post by gabmuks on 2014-08-14
> **kansasnoob said:**
> Right, look there again:

[http://ubuntuforums.org/showthread.php?t=2239290&p=13097139#post13097139](http://ubuntuforums.org/showthread.php?t=2239290&p=13097139#post13097139)



Then try those commands, rinse-n-repeat as needed.

Success!!!

I typed in the third command you gave.
After about an hour, the installation was finished.

I rebooted and I now have Ubuntu 14 and all of my documents are intact!!


Thank you Sir for all of your help!
I will mark my threads solved.

Thanks again.

---

### Post by kansasnoob on 2014-08-14
> **gabmuks said:**
> Success!!!

I typed in the third command you gave.
After about an hour, the installation was finished.

I rebooted and I now have Ubuntu 14 and all of my documents are intact!!


Thank you Sir for all of your help!
I will mark my threads solved.

Thanks again.

You're welcome, it's good to win one once in a while :)

---

