---
title: "Login failure."
date: 2013-11-30
forum: Installation &amp; Upgrades
---

### Post by jamseal32 on 2013-11-30
I have installed Ubuntu 13.10 three different times using NebootCd 5.2 and am still having the same problem.  Everything went fine until I reboot and get to the black login screen.  I enter Username and password and everything seems fine.  Then it takes me down the screen and gives me a what appears to be a shell prompt ending in (~$).  I don't know what to enter after this.  I've already given it my Username and password.  I guess it's asking me for some command to enter the system.  I'm new with Linux and don't understand the language yet. I'm a patient person but this is getting monotonous not to mention time consuming. Please help.

---

### Post by heir4c on 2013-11-30
Try:
```
startx
```

If that not work then reboot and boot up from recovery mode from the Grub menu. And when you get the little menu click just Enter to boot to the Desktop. (I hope you end up in the Desktop) There you can go to see the additional drivers Tab in Software&Updates via the Dash (UbuntuLogo on the top left). maybe there is some problem with it or you have no more support for your graphics card and can't use the non-free drivers anymore.
What graphics card have you?

---

### Post by jamseal32 on 2013-11-30
I tried startx which it downloaded but still does the same thing.  But now it won't even enter the Grub menu.  Goes straight to the purple screen with Ubuntu and the blinking dots.  After that back to the black login screen where I enter Username and password then down to prompt where it appears to ask for a further command.

---

### Post by Bashing-om on 2013-11-30
jamseal32; Hi ! My welcome to the forum.

Something is not at all right ! You should boot to a GUI login, not to a termianl.

To start the trouble shooting process; At that terminal go ahead and login (username and password) and enter the terminal command:
```

sudo service lightdm start

``` Which might start the GUI.
You will be required to enter your pass word again; "sudo" = Super User DO -> granting you admin privileges. There will be no response to the screen. Enter your pass word blindly and then the enter key.This is normal, just another security feature of linux.

What results ? Post back with any errors the system generates to the screen.

Also possible the system can not load a graphics driver, will see.

[INDENT][INDENT]one step at a time
[/INDENT][/INDENT]

---

### Post by jamseal32 on 2013-11-30
When it asks for my password (sudo) again after i type the service command, should i just enter my password or "sudo"=Super User DO-> ?  Sorry but i'm illiterate.

---

### Post by jamseal32 on 2013-11-30
This thing keeps looking for something after I enter my password.    It is prompting me with: james@boxFrontier4224:~$    Nothing I've entered after that seems to work other than downloading other things such as Startx.

---

### Post by heir4c on 2013-11-30
Downloading startx ?? This is the command to start up the x-server.


When you seeing this:
james@boxFrontier4224:~$
You are indeed already IN your system. But in "text mode" 
Type:
```
ls
```
Can you see your folders in your home folder?
Something like this is what you must see:
```
Afbeeldingen  Downloads     Pictures  
Desktop       examples.desktop   Public     Videos
Documents       Music     Templates
```

After that you must see again the prompt:
james@boxFrontier4224:~$ 
So, type:
```
sudo service lightdm start
```
like bashing-om already says.
Now your password will be asked. (That one that you used to log in)

---

### Post by jamseal32 on 2013-11-30
After typing "ls" I just get the james@boxFrontier4224:~$ again.

---

### Post by Bashing-om on 2013-11-30
jamseal32; Yuk !

That does not bode well !

Tell us once more that you are at this prompt "james@boxFrontier4224:~$"
You type ls and get no output (???).

Let's see if heir4c is in agreement.

In that case the system must not be fully installed. Time to back up, reqroup, dot the "i's" and cross the "t's".
Verify the .iso file's integrity: Documentation;
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Are you burning to DVD, USB or some other install medium ?

Can you boot the liveDVD to "try ubuntu" mode ?

Looking ahead for what to expect;
Are you installing as ubuntu the sole operating system or dual booting ? 

working to get you fully installed.
[INDENT][INDENT]ain't nothing but a thing[/INDENT][/INDENT]

---

### Post by steeldriver on 2013-11-30
What image did you install exactly and where did you get it? "Netboot 5.2" sounds more like a Debian (Lenny?) release than an Ubuntu one. Also a server installation would have nothing in the user's home directory by default - the Documents / Downloads / Music etc directories are specific to the desktop install process AFAIK.

---

### Post by Bashing-om on 2013-11-30
Oh ! 
There's that "j" to jot ! ..  Never even crossed my mind !
Once more steeldriver's voice of experience.

[INDENT][INDENT]cause and effect
[/INDENT][/INDENT]

---

### Post by jamseal32 on 2013-11-30
This is an old Dell Dimension 110 80g that had xp on it.  Long time ago i wiped the hdd and put Mint and Puppy on it.  Worked fine.  But I'm always messing with things and I wiped them (3 times) and wanted to put Ubuntu.  This time I think everything came off including MBR and Grub, I guess.  Now it won't load from Live Operating sytem cd's (Ubuntu, Mint, Win7). The only thing that will load are cd's like Boot Repair, Ubuntu recovery with Gentoo on it, and the NetBoot Cd 5.2 which you can download Ubuntu,Debian,SysLinux, Tiny something and a couple other systems. I'm putting 0's on it right now to start over.  I do have patience but tell me if I'm wasting my time.  Don't mean to drag on but I'm awfully stubborn.  I do appreciate you help greatly. And I will learn the language, someday. Thanks.

---

### Post by Bashing-om on 2013-11-30
jamseal32; Good spirit .

I know nothing of NetBoot Cd 5.2, But any way I can help. I will .

Old hardware though, you might consider a lighter distro ... I can recommend Lubuntu. Or, with your experience how about a minimal install and roll what you want installed into that core install ?
 
The high end (u)buntu and (k)ubuntu are resource hungry. You will not have a good user experience installing onto old hardware.

[INDENT][INDENT]hey, just my thoughts
[/INDENT][/INDENT]

---

### Post by heir4c on 2013-12-01
How many RAM on the Dell?

Just burn a cd with Lubuntu on.
If you can boot up from usb than you can make one with Unetbootin or Multisystem.

---

### Post by jamseal32 on 2013-12-01
Hi guys,  I've been working and just got back to my computer.  Back to square one.  I burned MultiSystems to a Flash and it won't boot, neither will live cd's (all I have now is DVD's), maybe that's why they won't boot.  Maybe something wrong with my USB's but my mouse and keyboard are working fine.  Only things that will boot are the Boot Repair CD, Ubuntu recovery with Gentoo(if I new the language I might get somewhere with this one). The only other one that will boot is the Netboot CD.  I was counting on the MultiSystems but no luck.  This machine has 2G of ram with 80g hdd.  Like I said, I've had Mint and Puppy on it as a  dual boot and didn't have any trouble.  I know Puppy is very small but Mint...?  Sure wish now I would have left them alone.  I'm not licked yet.  Still baffles me about only taking certain cd's and not pendrives at all.  Used too.

---

### Post by Bashing-om on 2013-12-01
jamseal32; Hey,

Trying to hang with you !

Look, we are talking real low end with a Dell Dimension B110 !
> 
All models feature a 2.53GHz Intel Celeron D 325 processor, integrated graphics


So for us .. let's not even think of trying to install anything above the level of Lubuntu, not to even talk yet of "integrated graphics" and what that might mean.

As you can not boot a CD, I am at a disadvantage to assist as that is the only means I have ever employed for installs.
As a thought to get the CD drive to boot, have you thought about resetting bios back to defaults and see if that has any good results ?

[INDENT][INDENT]any port in a storm
[/INDENT][/INDENT]

---

### Post by jamseal32 on 2013-12-02
Bashing-om; Hi,
Tried resetting bios to no avail.  Must be harware problem somewhere.  Worn out computer.  I'll keep plugging away tho.  Thanks.  At least it still turns on.  Ha

---

### Post by Bashing-om on 2013-12-02
jamseal32; Hello .

Where there is life there is hope ! 
(update bios ??)

---

### Post by jamseal32 on 2013-12-03
Bashing-om; Hey,
Life is happiness!  Finally have an Operating system on the old Dell.  Don't know how I did it but the Netbootin was were it came from.  If I remember correctly, I downloaded the Netbootin program off of the Unetbootin list of programs.  It's just a great relief to be making just a little progress.  Persistence sometimes pays off.   It's the "Debian" operating system and I don't care how much memory it eats because it sure beats a blank screen and an awful lot of frustration.  The dead talk!

---

### Post by Bashing-om on 2013-12-03
jamseal32: Bliss !

Great ya got it sorted out, debian is a great distro too ! .. I just prefer the support of the ubuntu network, but, it is all linux !

If you are happy with this as a solution, please mark this thread as solved - 1st post -> thread tools.
Or - Hey - open another thread and we can work on getting ya Lubuntu installed, still !

and we will go 
[INDENT][INDENT]merrily on our way[/INDENT][/INDENT]

---

