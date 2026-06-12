---
title: "Restore My ubuntu version !!"
date: 2010-09-24
forum: Installation &amp; Upgrades
---

### Post by siimoz on 2010-09-24
hi 
is there any way to restore my os to it's default without removing any updates
i just wanna remove the external changes in programs and installing some apps 
is that possible ??
i'm using ubuntu 10.04
thank you

---

### Post by tommcd on 2010-09-25
> ... i just wanna remove the external changes in programs and installing some apps 
is that possible ??

Well, it would help a great deal if you could tell us exactly what you mean by *external changes* and *installing some apps*.
How is anyone supposed to know what you are talking about here ???
If you have any 3rd party repos in your */etc/apt/sources.list*, or your 
*/etc/apt/sources.list.d* directory, you could start by removing those.
You need to really explain what exactly is your problem here ??!!??

---

### Post by siimoz on 2010-09-25
> **tommcd said:**
> Well, it would help a great deal if you could tell us exactly what you mean by *external changes* and *installing some apps*.
How is anyone supposed to know what you are talking about here ???
If you have any 3rd party repos in your */etc/apt/sources.list*, or your 
*/etc/apt/sources.list.d* directory, you could start by removing those.
You need to really explain what exactly is your problem here ??!!??
okay an' srry i'm new here
i tired to install my unsupported video card 
so i installed lots of things i don't need 
like xorg and things like that
so i wanna restore my version to it's default without removing system updates :)

---

### Post by grahammechanical on 2010-09-25
I am not an expert, so take the advice of others over mine. The really drastic method is to re-install and then update. Of, course you could wait for 10.10 to come out. Backup your data.

I have a minor problem getting 3D effects working. It works perfectly on an installation on a partition that I use for testing upgrades but on my working installation any attempt to get 3D effects results in dialog boxes freezing and window resizing icons becoming missing. I am guessing that there is something conflicting with something else.

So ... before upgrading to 10.10 I am going to archive my data and record my settings (email stuff, passwords, etc), then when I upgrade I can mark both the / partition and the /home partition to be formatted to give a clean install. May be you could do the same but it is a drastic solution.

Regards.

---

### Post by FlameReaper on 2010-09-25
> **siimoz said:**
> okay an' srry i'm new here
i tired to install my unsupported video card 
so i installed lots of things i don't need 
like xorg and things like that
so i wanna restore my version to it's default without removing system updates :)

Hmm. Just curious, what's the model of your video card?

---

### Post by coffeecat on 2010-09-25
Are the things you no longer need causing problems? If no, then forget about them. They won't slow the system down - this is not Windows.

By the way, don't bother uninstalling xorg. It's simply what's called a metapackage and you need that to keep the xserver updated. Which is what the GUI is based on. You do want a GUI, don't you?. :wink:

---

### Post by tommcd on 2010-09-26
> **siimoz said:**
> 
i tired to install my unsupported video card 
Please tell us the exact make and model number of your video card (ATI, Nvidia, Intel, Sis, or something else???). Also tell us exactly what you tried to install to get it working.
It is quite likely that we (myself + the rest of the Ubuntu forums!!!) can get your video card working. Exactly what problems are you having with video anyway?
> **siimoz said:**
> 
so i installed lots of things i don't need 
like xorg and things like that ...
Again, please tell us exactly what you installed that you want to get rid of. You need to be specific here. Nobody can know exactly what you installed or what you want to remove unless you tell us. 
If these packages that you installed are not causing you any problems, there is no harm in just leaving them on your system.
> **siimoz said:**
> 
so i wanna restore my version to it's default without removing system updates :)
According to OldFred (who really knows his stuff!!!) you can get a list of all the packages you installed yourself by running this command in the terminal:
```
aptitude search '~i!~M'

```
See post #3 here:
[http://ubuntuforums.org/showthread.php?t=1574849](http://ubuntuforums.org/showthread.php?t=1574849)

---

### Post by siimoz on 2010-09-26
> **tommcd said:**
> Please tell us the exact make and model number of your video card (ATI, Nvidia, Intel, Sis, or something else???). Also tell us exactly what you tried to install to get it working.
It is quite likely that we (myself + the rest of the Ubuntu forums!!!) can get your video card working. Exactly what problems are you having with video anyway?

Again, please tell us exactly what you installed that you want to get rid of. You need to be specific here. Nobody can know exactly what you installed or what you want to remove unless you tell us. 
If these packages that you installed are not causing you any problems, there is no harm in just leaving them on your system.

According to OldFred (who really knows his stuff!!!) you can get a list of all the packages you installed yourself by running this command in the terminal:
```
aptitude search '~i!~M'

```
See post #3 here:
[http://ubuntuforums.org/showthread.php?t=1574849](http://ubuntuforums.org/showthread.php?t=1574849)
thank you :)
my video card is (ATI 9550 )
i searched every where to install it >> to have 3d desktop and other effects
and i installed lot's of things >> like kernel and xorg 

so is there any way to install it ? ,, 
i'm new ubuntu user and this is the only prob i'm facing from long time ago
i'm using Ubuntu 10.04 LTS .. 
thx

---

### Post by Mark Phelps on 2010-09-27
> my video card is (ATI 9550 ) so is there any way to install it ? ,, 

Basically, NO.  Not in 10.04 and not in 10.10, either.

AMD dropped proprietary driver support for your card long ago.  The only driver available now is the one already installed on your machine -- the open-source driver.

Don't download or otherwise try to force the installation of any other ATI/AMD video driver.  Doing so will only trash your display and force you to spend a LOT of time and effort restoring the same drivers you already have in place.

---

### Post by siimoz on 2010-09-27
but this is a big mistake in ubuntu !!
they should make the Os to do our needs
not us buy the things they support !

---

### Post by ezsit on 2010-09-27
> but this is a big mistake in ubuntu !!
they should make the Os to do our needs
not us buy the things they support !

What? How many driver disks or downloads have you had to go hunt for after installing Ubuntu? Usually NONE. Sometimes the graphics driver, but that installation routine is built into Ubuntu in the Restricted Drivers app. I'd say Ubuntu trumps Windows any day of the week in this regard.

Why would you not buy hardware that is compatible with the operating system you want to use. I only shop for and buy hardware that is Linux compatible, that way I do not have problems. I see a little research on my end before I make purchases to be far easier than troubleshooting a problem later.

I really do not understand your problem. You want Ubuntu to read your mind and work with every possible hardware combination you may have without any issues? Software development does not work that way, whether open or closed source.

---

### Post by siimoz on 2010-09-28
> **ezsit said:**
> What? How many driver disks or downloads have you had to go hunt for after installing Ubuntu? Usually NONE. Sometimes the graphics driver, but that installation routine is built into Ubuntu in the Restricted Drivers app. I'd say Ubuntu trumps Windows any day of the week in this regard.

Why would you not buy hardware that is compatible with the operating system you want to use. I only shop for and buy hardware that is Linux compatible, that way I do not have problems. I see a little research on my end before I make purchases to be far easier than troubleshooting a problem later.

I really do not understand your problem. You want Ubuntu to read your mind and work with every possible hardware combination you may have without any issues? Software development does not work that way, whether open or closed source.
okay . thank you :)

---

### Post by mörgæs on 2010-09-28
> **siimoz said:**
> but this is a big mistake in ubuntu !!
they should make the Os to do our needs
not us buy the things they support !

As explained in post 9, the problem is not Ubuntu but AMD.

---

### Post by leeb9972 on 2010-09-28
> **Mark Phelps said:**
> Basically, NO.  Not in 10.04 and not in 10.10, either.

AMD dropped proprietary driver support for your card long ago.  The only driver available now is the one already installed on your machine -- the open-source driver.

Don't download or otherwise try to force the installation of any other ATI/AMD video driver.  Doing so will only trash your display and force you to spend a LOT of time and effort restoring the same drivers you already have in place.

I upgraded from 10.4 to 10.10beta with ATI driver installed, kept getting black login screen, so decided to reinstall 10.4 then upgrade to 10.10beta without ATI driver and it worked. 
Works well, i do get an ATI error on boot up, but i ignore, any method i can use to get rid of this message?

---

