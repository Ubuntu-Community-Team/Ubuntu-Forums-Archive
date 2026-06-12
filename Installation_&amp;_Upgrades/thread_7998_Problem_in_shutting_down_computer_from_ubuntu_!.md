---
title: "Problem in shutting down computer from ubuntu !"
date: 2004-12-13
forum: Installation &amp; Upgrades
---

### Post by ikoyk on 2004-12-13
When I want to shut down my computer while in ubuntu-Linux, It displays after a minute a message "Power Down Pc" but after that my computer doesn't respond any more and I have to restart again in my Win-Xp, so as to properly shut down my computer. I follow the shutting down procedure exactly, but still something goes wrong(Computer-Log Out -Shut down). Can you help me?

---

### Post by hashimoto on 2004-12-13
[QUOTE=ikoyk]When I want to shut down my computer while in ubuntu-Linux, It displays after a minute a message "Power Down Pc" but after that my computer doesn't respond any more and I have to restart again in my Win-Xp, so as to properly shut down my computer. I follow the shutting down procedure exactly, but still something goes wrong(Computer-Log Out -Shut down). Can you help me?[/QUOTE]
 I had the same problem: The shut down process ended with prompt "acpi_power_off called" or "Power off". After several tests I found that to shut down my PC the proper way I must add "acpi=on nolapic" after the boot commands at /boot/grub/menu.lst .

BR
Hashimoto

---

### Post by zenwhen on 2004-12-13
My computer just turns back on when I shut it down. Thats my only Ubuntu issue.

---

### Post by talex004 on 2005-02-24
The way I did it (after failing all other methods described on this forum):
acpi=off appended to kernel's boot-params
apm appended in /etc/modules
It finally worked :)

---

### Post by bored2k on 2005-02-24
[QUOTE=talex004]The way I did it (after failing all other methods described on this forum):
acpi=off appended to kernel's boot-params
apm appended in /etc/modules
It finally worked :)[/QUOTE]


could u please explain in a more "n00bish" please  :confused: 
i supposedly did that and got no rsults

---

### Post by tdell on 2005-02-24
I have the same problem and it in fact is the one thing left that is preventing me from deletng XP all together. I have tried all these suggestions and a few others and NONE have worked.
As far as I can determine this is caused by a bug in the 2.6.8 kernel I guess will will have to upgrade the kernel to fix the problem once and for all.

Tom

---

### Post by bored2k on 2005-02-24
Ok i used this solution from the unofficial guide and guess what...WORKED !! :mrgreen: 

Q: acpi_power_off called

>  $ sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
$ sudo gedit /boot/grub/menu.lst 

Find this section

>  ...
title           Ubuntu, kernel 2.6.8.1-4-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.8.1-4-386 root=/dev/hda1 ro quiet splash
... 



Replace with the following lines

>  title           Ubuntu, kernel 2.6.8.1-4-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.8.1-4-386 root=/dev/hda1 ro quiet splash acpi=off apm=off 

Save the edited file 
>  $ sudo cp /etc/modules /etc/modules_backup
$ sudo gedit /etc/modules 

Append the following line at the end of file
> apm 

Save the edited file 

** really worked**!!

btw i have a linux-686 kernel, so i did it on that one and left 386 the same just in case, but i did work on 686 !

---

### Post by tdell on 2005-02-24
Been there,done that, didn't work for me.

Tom

---

### Post by Nightfall on 2005-02-24
[QUOTE=bored2k]Ok i used this solution from the unofficial guide and guess what...WORKED !! :mrgreen: 

Q: acpi_power_off called

 

Find this section

 



Replace with the following lines

 

Save the edited file 
 

Append the following line at the end of file
 

Save the edited file 

** really worked**!!

btw i have a linux-686 kernel, so i did it on that one and left 386 the same just in case, but i did work on 686 ![/QUOTE]

Oh, this works for me too!!!!
The pc shuts down... but NETWORK WORKS NO MORE after reboot!!!
??? 
I mean... N-E-T-W-O-R-K... 
It says [ OK ] when it brings up networking, but Internet is KO then...

---

### Post by talex004 on 2005-02-25
Well, I'm on dial-up, and it still works.

There is one more way to shut-down, without windows.
In grub's menu, press c (console), and type halt.
You can also append it to the /boot/grub/menu.lst:
```

title Power Off
halt

```

---

### Post by tdell on 2005-02-27
[QUOTE=bored2k]Ok i used this solution from the unofficial guide and guess what...WORKED !! :mrgreen: 

Q: acpi_power_off called

 

Find this section

 



Replace with the following lines

 

Save the edited file 
 

Append the following line at the end of file
 

Save the edited file 

** really worked**!!

btw i have a linux-686 kernel, so i did it on that one and left 386 the same just in case, but i did work on 686 ![/QUOTE]


Tried this the only difference is instead of sying acpi_power_off called it now says Power Down and then still nothing!

Tom

---

### Post by Ominus on 2005-02-28
[QUOTE=bored2k]Ok i used this solution from the unofficial guide and guess what...WORKED !! :mrgreen: 

Q: acpi_power_off called

 

Find this section

 



Replace with the following lines

 

Save the edited file 
 

Append the following line at the end of file
 

Save the edited file 

** really worked**!!

btw i have a linux-686 kernel, so i did it on that one and left 386 the same just in case, but i did work on 686 ![/QUOTE]
 Well... i did it..... it worked.... but my soundcard (Creative Audigy SB) stops working... (when booting it says "No soundcards found".. something like that..)  i erased the changes.. and my soundcard worked... now... how can i make BOTH works (soundcard and shutdown)???

---

### Post by Ominus on 2005-02-28
[QUOTE=bored2k]Ok i used this solution from the unofficial guide and guess what...WORKED !! :mrgreen: 

Q: acpi_power_off called

 

Find this section

 



Replace with the following lines

 

Save the edited file 
 

Append the following line at the end of file
 

Save the edited file 

** really worked**!!

btw i have a linux-686 kernel, so i did it on that one and left 386 the same just in case, but i did work on 686 ![/QUOTE]


 Well... i did it..... it worked.... but my soundcard (Creative Audigy SB) stops working... (when booting it says "No soundcards found".. something like that..)  i erased the changes.. and my soundcard worked... now... how can i make BOTH works (soundcard and shutdown)???

---

### Post by tdell on 2005-03-01
Well,   I bit the bullet and upgraded to Hoary, problem solved all works great now. I guess I can finally delete my XP partition.

Tom

---

### Post by zack18 on 2005-03-01
i have hoary ubuntu installed and everything seems to work fine (amd64-general), except i'm unable to shutdown the computer without pressing the power button on the case.

from the ubuntu login screen, i select to shutdown computer, and it proceeds to ask my for the password... i type the password, and it doesn't do anything... repeat, etc until i lose patience and press the power button.

are you all experiencing this also?

---

### Post by bored2k on 2005-03-01
[QUOTE=zack18]i have hoary ubuntu installed and everything seems to work fine (amd64-general), except i'm unable to shutdown the computer without pressing the power button on the case.

from the ubuntu login screen, i select to shutdown computer, and it proceeds to ask my for the password... i type the password, and it doesn't do anything... repeat, etc until i lose patience and press the power button.

are you all experiencing this also?[/QUOTE]

U can also try this , type ALT+F3 to get  a Shell , put ur username/passwd
enter > #sudo su  and type > #shutdown -h now .

---

### Post by Nighthawk on 2005-03-01
I had the same problem on my system, and none of the fixes above helped.

In the BIOS setup, under "Power Management", I had "Advanced Power Management" set to "Disabled".    I changed it to "Enabled", now shutdown works fine.

Even if this doesn't fix things for you - there is no reason to bring Windows up just to shutdown the system.   Once it says "Power Down", the system is at a safe point to turn off -  just hold down the power button for  7 seconds (or so), and the system will turn off.

---

### Post by tdell on 2005-03-01
[QUOTE=Nighthawk]I had the same problem on my system, and none of the fixes above helped.

In the BIOS setup, under "Power Management", I had "Advanced Power Management" set to "Disabled".    I changed it to "Enabled", now shutdown works fine.

Even if this doesn't fix things for you - there is no reason to bring Windows up just to shutdown the system.   Once it says "Power Down", the system is at a safe point to turn off -  just hold down the power button for  7 seconds (or so), and the system will turn off.[/QUOTE]

Some people, including myself, do not want to have to PTFB.

Tom

---

### Post by Funraiser on 2005-03-02
I found something really strange on the installation of Ubuntu, which I did 3 times already: unless I don't set/change/enable root user password with "sudo passwd root" I can't shutdown ! I can't either restart gnome with Ctrl ALt Backspace. But if I do the "sudo passwd root" command, then everything works fine...weird isn't it?

So the following might work: open the terminal and write : sudo passwd root
then choose a password for the root, confirm.
Then reboot (no shutdown here , but reboot).
And then follow the instructions on ubuntuguide.org for the acpi_power_off_called.
Restart.

It worked for me  8-)

---

### Post by Seazzy on 2005-03-02
[QUOTE=Nighthawk]I had the same problem on my system, and none of the fixes above helped.

In the BIOS setup, under "Power Management", I had "Advanced Power Management" set to "Disabled".    I changed it to "Enabled", now shutdown works fine.

Even if this doesn't fix things for you - there is no reason to bring Windows up just to shutdown the system.   Once it says "Power Down", the system is at a safe point to turn off -  just hold down the power button for  7 seconds (or so), and the system will turn off.[/QUOTE]

After  trying everything else on this thread, I finally got my computer to turn itself off by changing the Power Management settings in BIOS to APM/APCI. Thanks for the suggestion, does anyone know if the settings have anything to do with the way ubuntu installs itself?

---

