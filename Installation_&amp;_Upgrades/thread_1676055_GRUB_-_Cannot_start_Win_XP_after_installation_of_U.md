---
title: "GRUB - Cannot start Win XP after installation of UBUNTU 10.10"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by Strolchi on 2011-01-26
Hello,
after I finally successfully installed ubuntu, I cannot start Windows from the GRUB start menue.

Since I am an absolute beginner, please please, help.

BR

Strolchi

---

### Post by Quackers on 2011-01-26
When booting do you get a grub menu, or does Ubuntu boot up directly?
Have you run ```
sudo update-grub
``` from the terminal, in Ubuntu?

---

### Post by Strolchi on 2011-01-26
Thanks for that ultrafast reply,

I get a full normal menue, when i select win, ubuntu is loaded. Probably I should mention that after installation a system update was installed (from .22 to 24), but in my opp. that should have nothing to do with grub.
Sorry for my typing, I have to do it with my left hand only because I broke the right yesterday.
BR
Strolchi

---

### Post by Logiwonk on 2011-01-26
Out of curiosity, which install options did you use when you installed Ubuntu to start with (e.g. did you give it its own hard drive, did you use the advanced partition editor?)?

---

### Post by Quackers on 2011-01-26
There is an entry for Windows in the grub menu? When you choose that, Ubuntu boots, is that correct?

---

### Post by Strolchi on 2011-01-26
Hello Logiwonk,
I selected:
1.   next to another op system
2.   boot drive c: with Win XP
3.   for all other prim partitions as recommended

There is one thing that should be mentioned. There is a second drive with a mbr on it. Could it be that that drive (mrr) disturbs grub.

Otherwise Win XP was a clean new install, the same for UBUNTU.

BR

Strolchi

---

### Post by Strolchi on 2011-01-26
Hello Quakers,

yes thats correct, its boots UBUNTU.

Strolchi

---

### Post by Strolchi on 2011-01-26
Hello Quakers,
you asked  me if I ran this grub update routine 
sudo update-grub
no I did not, I am a beginner.

What does it do it.

---

### Post by drs305 on 2011-01-26
"sudo update-grub" updates the Grub2 menu you see during boot. It runs all the executable scripts in the /etc/grub.d folder. It's actually a 'stub' for "grub-mkconfig -o /boot/grub/grub.cfg" but it's easier to just type "update-grub" as root.

When you make changes in /etc/default/grub or to other grub2 configuration files, the actual menu you see (/boot/grub/grub.cfg) is not changed until this command is run.

Sometimes after installing Grub2 it does not see all the other operating systems on the computer. Running the update-grub command will recheck the system for other OS's and usually finds them the second time around.

---

### Post by Strolchi on 2011-01-26
Thank you,
good explanation, although it is a bit high for a beginner. I will try it right now.

Thank you.

---

### Post by _Impact_ on 2011-01-26
Cmon guys, you gotta help this guy, his window 7 won't start and his right hand is broken!!! :lolflag:

---

### Post by Strolchi on 2011-01-27
Meanwhile we have new day.

I tried the sudo update-grup program and got a new surprise.
At the end when the system askes for a password, it does not accept the entered characters. 
What to do now. In all other cases the password work as supposed.

I am logged in as admin.

Thanks in advance

---

### Post by drs305 on 2011-01-27
> **Strolchi said:**
> Meanwhile we have new day.

I tried the sudo update-grup program and got a new surprise.
At the end when the system askes for a password, it does not accept the entered characters. 
What to do now. In all other cases the password work as supposed.

I am logged in as admin.

Thanks in advance

If you are "logged in as admin" you would not use "sudo". Just run it as "update-grub". Otherwise, as a normal user the password would be your normal user password (which I imagine you already know).

---

### Post by Strolchi on 2011-01-27
Hello drs305,
Im the only reg. user on the system (with admin priviledges). When i tried as you suggestet the answer "is you must run it as root".
And here ends all my knowledge abaut LINUX.
I hope I dont drag too much on your nerves.

Strolchi

---

### Post by presence1960 on 2011-01-27
> **Strolchi said:**
> Hello drs305,
Im the only reg. user on the system (with admin priviledges). When i tried as you suggestet the answer "is you must run it as root".
And here ends all my knowledge abaut LINUX.
I hope I dont drag too much on your nerves.

Strolchi

We are going around in circles here. We need to see info about your setup and boot process.

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Move the boot info script to the desktop.
3. Open a terminal (Applications > Accessories > Terminal) and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` You can copy/paste this command to terminal

 This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by kansasnoob on 2011-01-27
Do we have multiple threads going here:

[http://ubuntuforums.org/showthread.php?p=10402746#post10402746](http://ubuntuforums.org/showthread.php?p=10402746#post10402746)

---

### Post by Elfy on 2011-01-27
> **kansasnoob said:**
> Do we have multiple threads going here:

[http://ubuntuforums.org/showthread.php?p=10402746#post10402746](http://ubuntuforums.org/showthread.php?p=10402746#post10402746)

Not any longer - that one is now closed.

---

### Post by presence1960 on 2011-01-27
> **kansasnoob said:**
> Do we have multiple threads going here:

[http://ubuntuforums.org/showthread.php?p=10402746#post10402746](http://ubuntuforums.org/showthread.php?p=10402746#post10402746)

The admin forestpiskie closed that thread...lol

---

### Post by Rubi1200 on 2011-01-27
> **kansasnoob said:**
> Do we have multiple threads going here:

[http://ubuntuforums.org/showthread.php?p=10402746#post10402746](http://ubuntuforums.org/showthread.php?p=10402746#post10402746)
For a minute I also suspected there were multiple accounts being created by the same person too.

Now **that** would have been fun to deal with; multiple grub personality syndrome.

---

### Post by Strolchi on 2011-01-27
Hello Presence 1960,
sorry, the same thing happens. I am ask to give my password, but char. are not written back.

Next I will try same thing, using the "live cd"

BR
Strolchi

---

### Post by presence1960 on 2011-01-27
> **Strolchi said:**
> Hello Presence 1960,
sorry, the same thing happens. I am ask to give my password, but char. are not written back.

Next I will try same thing, using the "live cd"

BR
Strolchi

There are no characters shown when typing password for security purposes. Just type your password and press Enter.

---

