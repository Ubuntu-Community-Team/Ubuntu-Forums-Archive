---
title: "Computer not booting up properly after upgrade to 24.04"
date: 2024-11-19
forum: Installation &amp; Upgrades
---

### Post by brindle67 on 2024-11-19
Hi, i have a dual boot machine. I can still boot windows, but Ubuntu asks for login and password then it displays welcome to Ubuntu 24.04 and below documentation *management *support.
I am stuck now, help please

---

### Post by grahammechanical on 2024-11-19
May I suggest that at the Grub boot menu you select Advanced options for Ubuntu and then select a Linux kernel that has recovery mode. That should load the Friendly Recovery menu. Select Resume. That will load to a login screen using an open source video driver instead of a proprietary video driver. If that brings you to a working desktop open Software & Updates>Additional Drivers tab and disable the proprietary video driver and continue using the open source video driver. Or, select a different proprietary video driver. You need to be connected to the internet to do this.

Regards

---

### Post by brindle67 on 2024-11-20
Hi thanks for your reply. I just tried that, it took me back to the same login screen, the only difference was a larger font. Brian

---

### Post by Rubi1200 on 2024-11-20
Did you install Ubuntu with encryption on the partition?

When did this problem start? After a Windows update, after an Ubuntu update?

Need more details to try and figure out what went wrong and when.

Thanks.

---

### Post by brindle67 on 2024-11-20
Hi it had been working fine, rarely used windows anyway. This happened after upgrading to the latest supported version yesterday. I am sure i did a partition when installing ubuntu. Thanks Brian

---

### Post by richard76 on 2024-11-20
Sounds exactly the same as my problem, hope you can resolve it and let me know how.

---

### Post by Rubi1200 on 2024-11-20
When you get to the login screen try Ctrl+Alt+F3 to switch to another tty session and try logging in with your regular username and password. You may have to try a few F combos, 1-7.

Does that get you back to the desktop?

---

### Post by brindle67 on 2024-11-20
Hi, Yes I tried that f1-f7 no luck i am afraid, thanks Brian

---

### Post by yancek on 2024-11-20
[QUOTE] [This happened after upgrading to the latest supported version yesterday. I am sure i did a partition when installing ubuntu. /QUOTE]

How did you do this upgrade?  Did you do an update/upgrade to the newer release or did you download the iso file, write it to a usb and install to the same partition(s)?

---

### Post by Rubi1200 on 2024-11-20
At the GRUB screen press e to edit the boot line for Ubuntu and find this line:

```
linux /boot/vmlinuz-<version> root=<UUID> ro quiet splash

```
Add nomodeset after quiet splash and then Ctrl+X to save temporarily and resume the boot process.

If this works and you can then get to the login screen and the desktop we are a step further.

---

### Post by brindle67 on 2024-11-20
I did it via the invitation from the updater, i did the update first and then the upgrade. Thanks Brian

---

### Post by brindle67 on 2024-11-20
Stop the installation to the grub menu.
Press e to edit the menu entry you choose (e.g Install Ubuntu) and it will lead to edit the boot parameters.
Find the line which ends with quiet splash and add nomodeset in front of it. ...
Press Ctrl+X or F10 to boot with this new parameter
I will follow this. Brian

---

### Post by brindle67 on 2024-11-20
Hi after splash at the moment it says $vt_handoff. Do I delete this or insert nomodeset? Thanks Brian

---

### Post by Rubi1200 on 2024-11-20
When you press **e **is this what you see?

```
linux /boot/vmlinuz-<kernel-version> root=UUID=<uuid> ro quiet splash $vt_handoff



```

If yes, change it to this:
```
linux /boot/vmlinuz-<kernel-version> root=UUID=<uuid> ro quiet splash nomodeset

```

Then Ctrl+X to exit and boot.

Anything?

---

### Post by brindle67 on 2024-11-20
No luck, it tried. I had a glimpse of the purple boot screen, and then some lines of text with Plymouth in green, then back to the login. Is there a way of posting a screen shot?

---

### Post by 1fallen on 2024-11-20
> **brindle67 said:**
> No luck, it tried. I had a glimpse of the purple boot screen, and then some lines of text with Plymouth in green, then back to the login. Is there a way of posting a screen shot?
Get to a TTY session again and run this, I have a hunch this is a GDM issue.

That method was discribed by Rubi1200>>>Ctrl+Alt+F3 at the login screen.

In fact at that tty session please rum:
```
sudo apt purge gdm3
sudo apt install gdm3
```

---

### Post by brindle67 on 2024-11-20
> **yancek said:**
> [QUOTE] [This happened after upgrading to the latest supported version yesterday. I am sure i did a partition when installing ubuntu. /QUOTE]

How did you do this upgrade?  Did you do an update/upgrade to the newer release or did you download the iso file, write it to a usb and install to the same partition(s)?

---

### Post by brindle67 on 2024-11-20
Woo yes i am in, looks big and not a lot there, what's next to do please Brian

---

### Post by 1fallen on 2024-11-20
> **brindle67 said:**
> Woo yes i am in, looks big and not a lot there, what's next to do please Brian

Who are you replying to???

---

### Post by brindle67 on 2024-11-20
Sorry yes you, that seems to have got me to what looks like a safe screen, not sure if i should reboot?

---

### Post by 1fallen on 2024-11-20
> **brindle67 said:**
> Sorry yes you, that seems to have got me to what looks like a safe screen, not sure if i should reboot?

Yes please do reboot, we have to give the Acid test...lol

---

### Post by yancek on 2024-11-20
I think some of your posts are too cryptic and uninformative.  You need to post specific details of what you did and what changes you made and the results.  Did you get in by using the method of changing the grub entry by hitting the e key on the keyboard.  Did you write down exactly what you did.  That method is a one time change and when you reboot it will go back to the original entry so you need to make the change permanent by modifying the correct grub file.  More details are needed.

---

### Post by brindle67 on 2024-11-20
The acid has been neutralised... But cant see any files. Tool bar at the bottom but no files??

---

### Post by 1fallen on 2024-11-20
Open your terminal and run this:
```
ls
```
That should show what you have as your user.

---

### Post by brindle67 on 2024-11-20
Sorry I got in by
sudo apt purge gdm3
sudo apt install gdm3
I have rebooted but I cant see any files only the app tool bar on the bottom of the screen

---

### Post by brindle67 on 2024-11-20
I don't seem to have a terminal

---

### Post by 1fallen on 2024-11-20
Will a keyboard combo of [Ctrl + Alt +T] open one?

---

### Post by brindle67 on 2024-11-20
Yes that worked. I have a small list of some folders

---

### Post by brindle67 on 2024-11-20
I opened up Libre and went to recent documents it opened so files are there or should i say somewhere

---

### Post by 1fallen on 2024-11-20
Now run this, it seems your upgrade might be in-complete:
```
sudo apt update && sudo apt upgrade
```

---

### Post by brindle67 on 2024-11-20
I am in now
 sudo apt purge gdm3
sudo apt install gdm3
I did a restart, logged in but no files at the moment

---

### Post by brindle67 on 2024-11-20
I have done that, and restarted. All of my apps are there now, 
but no files

---

### Post by 1fallen on 2024-11-20
> **brindle67 said:**
> I am in now
 sudo apt purge gdm3
sudo apt install gdm3
I did a restart, logged in but no files at the moment

Why are you doing this?

 > **brindle67 said:**
> but no files
What Files? 
Please show me this:
```
ls /home/$USER
```
I  can't see what you see, you are my eyes

---

### Post by brindle67 on 2024-11-20
I don't know how to post a screen shot, it is difficult to describe. I can open Rhythm box and play music, but i have no file system or folders like:
Music>
Beatles>
Let it be>
Two of us>

---

### Post by 1fallen on 2024-11-20
I don't need or want a Screenshot.
```

sudo apt install ubuntu-desktop
```

And you can restore any missing file/folders you don't have now from your back-ups.

If you did not back-up before embarking on a On-Line upgrade to Noble well then that is a sad day. :( (It has been said many times there are risks with a Version Upgrade)

I was asked by another member here to see if I could get you in to your system, the rest I'll leave up to you.

Good Luck

---

### Post by richard76 on 2024-11-21
Hi Brindle67, keep on it, I'm sure we are not alone with this problem, I too followed the prompts assuming there would be warnings if things were not going to go smoothly. I look forward to an extract of the successfull steps that solved your problem, maybe the more knowledgeable members of the Forum could do an analysis of the problem and provide a step by step guide as to how to (a) avoid the problem whilst updating and (b) solve the problem for those of us that follow blindly into the update.

---

### Post by brindle67 on 2024-11-30
All stable now thanks very much for your help.

---

### Post by 1fallen on 2024-11-30
> **brindle67 said:**
> All stable now thanks very much for your help.

Can you add how you did this, it would be helpful to others as well. :)
Happy to hear your back in business though.

---

### Post by brindle67 on 2024-11-30
I followed your suggestions . first sudo apt purge gdm3
and then 
sudo apt install gdm3
I was in but no Desktop so
sudo apt install ubuntu-desktop

---

### Post by 1fallen on 2024-11-30
Thank You for that! :)

---

