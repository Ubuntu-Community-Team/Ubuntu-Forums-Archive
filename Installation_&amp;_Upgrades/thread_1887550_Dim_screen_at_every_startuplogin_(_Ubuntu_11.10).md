---
title: "Dim screen at every startup/login ( Ubuntu 11.10)"
date: 2011-11-27
forum: Installation &amp; Upgrades
---

### Post by Skopuningurin on 2011-11-27
Hi!

I just upgraded to 11.10 from 11.04. I like it so far, but I've noticed a problem. 
Every time I log in/start up, the screen is dim. Very dim. To solve this I go to system settings and then screen, and move the bar al the way to the right. Then it's bright again. But when I start up the computer again, it's the same dim. 

And it's like that on every start up. It's annoying. 
Is there a way to fix this?

My computer is Acer Aspire 6930G

---

### Post by Skopuningurin on 2011-11-27
bump

---

### Post by gdonwallace on 2011-11-27
I hope you get an answer to this as well.  I am having the same issue.

At first I thought it was because I was starting w/o the power plugged in, but it seems to do it even when plugged in.

I don't have Kubuntu configured for "power saver" mode, so I am not sure what the problem is.

---

### Post by cmcanulty on 2011-11-27
I have it too HP Laptop G72t but mine is worse there is no slider to get it bright. I need a fix

---

### Post by MAFoElffen on 2011-11-27
> **Skopuningurin said:**
> Hi!

I just upgraded to 11.10 from 11.04. I like it so far, but I've noticed a problem. 
Every time I log in/start up, the screen is dim. Very dim. To solve this I go to system settings and then screen, and move the bar al the way to the right. Then it's bright again. But when I start up the computer again, it's the same dim. 

And it's like that on every start up. It's annoying. 
Is there a way to fix this?

My computer is Acer Aspire 6930G

Try this:

1) edit rc.local
```

gksudo gedit /etc/rc.local

```
2) Add a line with this command before the line with EXIT 0 	
```

setpci -s 00:02.0 F4.B-0

```
Save and exit

3) Reboot.

---

### Post by cmcanulty on 2011-11-28
I have tried this fix and several others but they make it worse as then the screen brightness slider is gone and the only way I can get the screen back is to reinstall Ubuntu 11.10.Please fix this bug ad also provide an undo command as I have reinstalled several times trying to fix this.

---

### Post by philipum on 2011-11-29
Hi, 

I have a HP pavilon dv6 laptop. I have the same problem since upgrading ubuntu from 11.04 to 11.10. I also tried to burn a CD with a fresh ubuntu 11.10 and got the same at startup. It is as if the screen started on power save mode and stayed like that whatever I do. I can set the screen brightness to max and then I get barely enough brightness to be able to work normally. 

It seems that the symptoms correspond to this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/555709](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/555709)

Edit: I tried the proposed fix above, as well as the one proposed in the bug thread, it didn't make any difference.

---

### Post by cmcanulty on 2011-11-29
I tried  to study the commands that may get me to the right config files but I wasn't sure where to start I tried acpi and lspci and some etc files but don't know enough. I know it's not hardware as it works OK after I reset it with every login or boot.Many reports of this showed up so it seems Ubuntu would make it a priority fix but so far nothing. I tried xfce4 desktop and same thing Ubuntu is starting to be as frustrating as WIN I also lost sound on one computers upgrade.

---

### Post by Herbon on 2011-11-29
Bump

---

### Post by Skopuningurin on 2011-11-29
> **MAFoElffen said:**
> Try this:

1) edit rc.local
```

gksudo gedit /etc/rc.local

```
2) Add a line with this command before the line with EXIT 0 	
```

setpci -s 00:02.0 F4.B-0

```
Save and exit

3) Reboot.

This did not solve the problem for me.. :) More like removed the bar, so I'm not able to adjust the brightness of the screen :confused::confused:

---

### Post by cmcanulty on 2011-11-29
Me too now I can't even get it light is this going to go on forever? We need a fix

---

### Post by Skopuningurin on 2011-11-30
bump

---

### Post by cmcanulty on 2011-12-02
I made a long post on another forum but am putting a link here as I have tried a few other things and got it to not dim on logout and suspend but still dims at restart and shutdown. It dims right after the point in the boot process where the ubuntu name comes up and I am suspecting the nvidia driver that caused problems with google earth in 11.04 and I removed it. But apparently in 11.10 you cannot remove nvidia without removing the entire ubuntu desktop. Here is my link though several threads have been addressing this issue in different forums with no solutions.It must be a module that loads at a certain point in the boot process and happens on many different spec laptops though mine is a HP G72t[http://ubuntuforums.org/showthread.php?t=1862893&highlight=dim+screen]("http://ubuntuforums.org/showthread.php?t=1862893&highlight=dim+screen")
I run 10 library laptops with this spec and can't upgrade until this is fixed. I did my home laptop and discovered this bug.

---

### Post by Skopuningurin on 2011-12-03
Yeah. I guess we just have to wait until they fix it.. This is quite annoying.. We just have to bear with it until it's fixed.

---

### Post by Basher101 on 2011-12-03
okay guys so this is from another post from me on how to fix the brightness issue without the slider:

> type in a terminal: ```
sudo gedit /etc/rc.local
``` and there you will see at the very most bottom a red colored [COLOR="Red"]EXIT[/COLOR]. Just above that "exit" type the command ```
setpci -s 00:02.0 F4.B=00
``` and save the settings. Next file you will have to edit is your Grub config file. Type into a terminal ```
sudo gedit /etc/default/grub
``` there you will see different settings. Now look for the line that looks like this: [QUOTE]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" and add "acpi_osi=Linux" at the end so that the line looks like this after editing:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR="Green"]acpi_osi=Linux[/COLOR]"

this should fix your problem. the only thing that got BROKEN is the indicator app that shows you that "bar" of the brighntess and that it is reversed (UP arrow increses brightness and DOWN decreses the brightness). But this is a price i gladly pay to change the brightness.[/QUOTE]


regards

---

### Post by cmcanulty on 2011-12-03
Got it this works on my HP G72 t I have been researching this for days. I tried logout, restart, shut down and brightness setting was saved I followed the blue directions from this posted link I also installed xbacklight but think that wasn't needed.AS usual use at your own risk
[http://forums.linuxmint.com/viewtopic.php?f=42&t=45271]("http://forums.linuxmint.com/viewtopic.php?f=42&t=45271")

---

### Post by Skopuningurin on 2011-12-18
This soulutison didn't solve the issue, but it defently made it brighter :) I'll say that this issue is solved.
Thank you.

---

### Post by cmcanulty on 2011-12-18
Not solved for me at library it goes black and has to be restarted often. Is there a way to turn off all power saving features permanently for all users?

---

### Post by LousMX5 on 2012-06-29
No luck with these, or any other "fixes" /[SOLVED] I've come across.

I have a Samsung NC10 netbook, and every time it reboots or comes back out of hibernation I have the dim screen and it requires a lot of effort to get it back to a readable backlight level.

Has anyone come across a fix??  I like Ubuntu, except for these strange errors that impact lots of people that never seem to get fixed despite the complaints.

~Lou

---

### Post by speedwlk on 2012-06-29
Please have a look at
[http://forums.linuxmint.com/viewtopic.php?t=86813](http://forums.linuxmint.com/viewtopic.php?t=86813)

Look at the instructions under the header "**[COLOR=#008000]1m. Reduce laptop screen brightness persistently[/COLOR]**".

Of course you have to do the opposite.

Good Luck!

---

### Post by cmcanulty on 2012-06-29
try 

```
sudo gedit /etc/default/grub
```

then alter this line to make backlight =vendor as below
```

GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
```

I agree the annoying bugs are what turn off users not lack of all the fancy doodads they keep working on. Like lately one computer I have disables network manager at every reboot. Good luck

---

### Post by LousMX5 on 2012-06-29
Thanks gents, will let all know if either works -- will try the GRUB edit first since it's easiest :-)

---

### Post by LousMX5 on 2012-06-29
Thanks [cmcanulty]("http://ubuntuforums.org/member.php?u=36066")!

The grub edit worked, and now my keyboard brightness buttons even work properly now.

That particular line had "" after it, so I just added your suggestions and rebuilt the grub file.

The only initial drawback was that the screen backlight was completely off, but I knew after I typed my password and hit enter, I could try the keyboard brightness keys and then viola!

For others trying this, I had already made the previous GRUB changes noted earlier in the thread, this one was an add-on to that which worked for my Samsung NC10 netbook.

Thanks everyone!

~Lou

---

### Post by xubuntu84 on 2013-02-22
> **cmcanulty said:**
> try 

```
sudo gedit /etc/default/grub
```

then alter this line to make backlight =vendor as below
```

GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
```

I agree the annoying bugs are what turn off users not lack of all the fancy doodads they keep working on. Like lately one computer I have disables network manager at every reboot. Good luck

I know this is an older post, but I just wanted to let other users know that find this via Google that the above grub edit worked for me.  Just remember to run sudo update-grub after saving the file.  HP Pavilion dm4 running Ubuntu 12.04.  Thanks!

---

### Post by DoubleOhDave on 2013-05-17
I tried this edit (GRUB) and found it was already as shown.. but I still have the same problem. 
My machine is a Toshiba L40 - about 6 years old and running 12.04 
I found a temporary fix - by hitting the FN key and F7 at the same time when Ubuntu starts up it instantly brightens the screen. 

If only I could get this to work without having to do that at every start up it would be great!

---

### Post by odror on 2013-09-08
This works for me too on Hp envy 17t j000. There is only one problem. Now it is with maximum brightness.  Is there a way to make it less bright.

Thanks

---

### Post by sleepee on 2013-10-09
So that grub edit fixed the dim screen at startup for me as well..
But the only problem is that now I cannot adjust screen brightness, which is a problem because my computer boots with maximum brightness now.
I'm running Ubuntu 13.10 64-bit on a Lenovo u430 Touch.

---

