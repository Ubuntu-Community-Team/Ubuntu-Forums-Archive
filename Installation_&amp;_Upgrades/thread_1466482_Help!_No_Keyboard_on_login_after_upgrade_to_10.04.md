---
title: "Help! No Keyboard on login after upgrade to 10.04"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by mafia910 on 2010-04-30
I just upgraded to 10.04 from 9.04 and I cannot log in to the machine.  I tried launching the on-screen keyboard but it just flashes and disappears.  Anyone else having this issue?

I also tried attaching a different USB keyboard, but that didn't work either.  Any help would be appreciated.

---

### Post by pavera on 2010-04-30
Same issue.  Ubuntu running in vmware fusion.  After upgrade from 9.10 keyboard does not work at the login screen.

Also attempted a clean new install, same problem no keyboard at the login screen...

---

### Post by aglc2005 on 2010-04-30
Same problem for me. PS/2 keyboard works great, but any USB HID device does not.

---

### Post by Mike Beatty on 2010-04-30
Same here. :(
I did a fresh install of 10.04 in VMWare Player on Windows 7 host.
Anyone have any ideas on how to solve this?

---

### Post by auximage on 2010-04-30
I have this same problem.  Running in VMWare.  Was only able to log in after using the on screen keyboard.  Is there a fix out there for this problem?  Seems kind of silly to upgrade and be expected to not have use of a keyboard.. /c:

As far as using the on screen keyboard.  I had to select it and restart the machine a couple times before it remained on screen and I was able to use it.

---

### Post by auximage on 2010-04-30
Now that I've logged in, the keyboard works as normal.  Just thought that I would update that.  I will try rebooting to see if continues to be disabled on the login screen.




EDIT:  Upon reboot, keyboard still does not work on the login screen.  This is kinda a major bug I would think..

---

### Post by gregwa on 2010-04-30
same issue with 9.04 daily upgrade (NOT upgrade to 10.04).  Get login screen, once you log in, screen blinks, and asks you to log in.  Onscreen keyboard has same issue.  Can't log in at all

Kubuntu 9.10 is apparently having similar issues.

---

### Post by NoBugs! on 2010-04-30
Did you try booting 2.6.31 or another kernel other than 2.6.32? You can choose at the boot screen, by pressing down-arrow and choosing the older kernel. If 2.6.32 is the only kernel that doesn't recognize the keyboard, that is probably [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/571528").

---

### Post by jonathanhayward on 2010-04-30
Maybe Ubuntu needs to emulate an old feature in DOS...

"Keyboard failure error. Hit ESCAPE to abort, or RETURN to continue."

---

### Post by aglc2005 on 2010-04-30
> **NoBugs! said:**
> Did you try booting 2.6.31 or another kernel other than 2.6.32? You can choose at the boot screen, by pressing down-arrow and choosing the older kernel. If 2.6.32 is the only kernel that doesn't recognize the keyboard, that is probably [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/571528").

When I have access to my machine again I will have to give this a try and will let you know the results. That is very interesting.

---

### Post by Monkbel on 2010-05-01
The same problem is for me and also here: [http://ubuntuforums.org/showthread.php?t=1466442](http://ubuntuforums.org/showthread.php?t=1466442)

This bug basically renders 10.04 unusable for many. It's unexpected that LTS could have been shipped with such significant bug :).

The workaround that works for me is "virtual keyboard", that you can turn on from accessibility menu in bottom-right.

---

### Post by kermiac on 2010-05-01
Seems like it might be this bug.

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/548891]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/548891")

The workaround until this goes through the SRU process is to run the following command in your virtual machine ```
sudo dpkg-reconfigure console-setup
```

Please don't comment on the bug report as it has all of the information required to fix this. This is a "known issue" & is currently going through the normal SRU process to be released to lucid updates. If you are experiencing this issue you can click on the "affects me too" button at the top of the bug report.

---

### Post by jeffb503 on 2010-05-01
i up graded under vmworks/osx and had the same problem. i found the answer here:

[http://reformedmusings.wordpress.com/2010/04/24/keyboard-issues-with-ubuntu-lucid-10-04-and-vmware-workstation-7-0/](http://reformedmusings.wordpress.com/2010/04/24/keyboard-issues-with-ubuntu-lucid-10-04-and-vmware-workstation-7-0/)

i did what was suggested and now the keyboard works. one issue was i didn't have the shut down icon (to select console input) so i had to use the ubuntu on screen keyboard to log in - i got to it by selecting the universal access icon at the bottom; selected the on screen keyboard option; and rebooted ubuntu; the onscreen keyboard then appeared letting me log in and do the above fix.

-jeff

---

### Post by oldfred on 2010-05-01
I had this problem a year ago when I put a new motherboard in. It is BIOS settings. I was quickly swapping USB & ps/2 keyboard as the ps/2 worked for booting. There is a BIOS setting for USB keyboards that you need to change.

---

### Post by can_surmeli on 2010-05-02
Yeap. Exactly the same problem here.

I made my Ubuntu 10.04 LTS installation via Vmware Fusion on my Mac.

> 

i up graded under vmworks/osx and had the same problem. i found the  answer here:

[http://reformedmusings.wordpress.com...rkstation-7-0/]("http://reformedmusings.wordpress.com/2010/04/24/keyboard-issues-with-ubuntu-lucid-10-04-and-vmware-workstation-7-0/")

i did what was suggested and now the keyboard works. one issue was i  didn't have the shut down icon (to select console input) so i had to use  the ubuntu on screen keyboard to log in - i got to it by selecting the  universal access icon at the bottom; selected the on screen keyboard  option; and rebooted ubuntu; the onscreen keyboard then appeared letting  me log in and do the above fix.

-jeff     

I haven't tried the solution above but enabling the virtual keyboard and then after a reboot I typed in my password via the virtual keyboard so I was successful with the login process after some time with hassle.

The funny thing though is that my keyboard started working just fine when the system started. So that I'm not sure if this is a problem with Vmware Fusion or Ubuntu 10.04 LTS.

---

### Post by cheekybean on 2010-05-02
Same problem here with Dell Inspiron 6400 using Distribution upgrade option on Xubuntu.

Keyboard totally non functional.

Makes the distribution useless for me for now.  Had to revert to USB live distro until this is fixed by an update.

---

### Post by sarit431 on 2010-05-02
> **NoBugs! said:**
> Did you try booting 2.6.31 or another kernel other than 2.6.32? You can choose at the boot screen, by pressing down-arrow and choosing the older kernel. If 2.6.32 is the only kernel that doesn't recognize the keyboard, that is probably [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/571528").


er, it is a little hard to type the down arrow with no keyboard. I too have no keyboard at login screen after updating from 9.10. I am running Ubuntu in VMware under Win. 7. Once logged in using the onscreen keyboard my keyboard comes alive wonderfully.

---

### Post by Meghnaad on 2010-05-03
After a Lot of Google and My Friends (Dawood) Help I was Able to Solve the Problem.
I've Mentioned steps on Following Link
> [http://blog.ichinmay.com/2010/05/03/ubuntu-10-04-upgrade-from-9-10-usb-keyboard-mouse-problem/](http://blog.ichinmay.com/2010/05/03/ubuntu-10-04-upgrade-from-9-10-usb-keyboard-mouse-problem/)

**[COLOR="DarkRed"]Let me know if it helps you too[/COLOR]**

---

### Post by jstalnak on 2010-05-03
@Meghnaad -- Alas, my xorg log files shows that the config/udev never does load the keyboard/mouse! I made your suggested changes based on the pre-Lucid xorg log file, but that has made no difference. I can see from the present log file that the entries I added in the 05-evdev.conf file are being read (I actually see entries in the emulation set up section of the xorg log file that show the Identifiers of the entries I added, but I still have no keyboard or mouse. 

What is interesting is that I can ssh into the box, run x11vnc, and then vnc in and I DO have mouse and keyboard.

---

### Post by Zapboy on 2010-05-03
I had the same issue (both in Karmic and Lucid). I added noapic and noapci to the grub.cfg and my keyboard and mouse came alive on reboot. Since I am on a multiboot system, I just "e" to configure my boot options.

Just my two bits...

---

### Post by jstalnak on 2010-05-03
noapci noapic ineffective for me, still no keyboard mouse once login screen reached. Keyboard DOES work up to that point (can edit grub, etc.) but once X loads, they're both dead. And, interestingly, I can ssh into the box and run x11vnc, and then vnc into the box and I do have keyboard and mouse, but the keyboard shift key is not recognized. It is X, I've swapped keyboards and the problem remains.

Anyone know how to force a reinstall of the part of Ubuntu/X that's responsible for reporting hardware? Is that udev?

---

### Post by Meghnaad on 2010-05-04
> **jstalnak said:**
> @Meghnaad -- Alas, my xorg log files shows that the config/udev never does load the keyboard/mouse! I made your suggested changes based on the pre-Lucid xorg log file, but that has made no difference. I can see from the present log file that the entries I added in the 05-evdev.conf file are being read (I actually see entries in the emulation set up section of the xorg log file that show the Identifiers of the entries I added, but I still have no keyboard or mouse. 

What is interesting is that I can ssh into the box, run x11vnc, and then vnc in and I DO have mouse and keyboard.

Can you paste output of commands you executed ?
and contents of 05-evdev.conf ?

---

### Post by cgp1024 on 2010-05-13
I also had this problem, but for me, it turned out to be the xorg kbd_drv.so driver that couldn't be loaded.  I had a custom xorg.conf....

After booting in recovery mode (holding shift during boot), and removing /etc/X11/xorg.conf, they keyboard works again.

---

### Post by k_traxler on 2010-06-21
Today I updated my Ubuntu 10.04. The keyboard problem is FINALLY fixed!!! :roll:

---

### Post by Krzysztow on 2010-10-05
Just a hint, since this happened to me.

I'm using Ubuntu for quite some time and recently it happened the same as described before - I could login with keyboard, but it didn't work afterwards. I was looking for help on that and other forums and trying some possible solutions it occured that keyboard works but with a very long lasting pushes. I mean, I had to keep the button down for around 10 secs to get the character on the screen. 

Having noticed that, I went to System->Preferences->Keyboard and there  to Accesibility tab and unchecked "Only accept long keypresses". And now it works. Seems very easy but I spend some time (cursing) trying to get it working. Of course, this could be my fault (I don't say no), but now I cannot be sure. Otherwise, when it happens to someone else, here it is.

Bye,
Chris.

---

