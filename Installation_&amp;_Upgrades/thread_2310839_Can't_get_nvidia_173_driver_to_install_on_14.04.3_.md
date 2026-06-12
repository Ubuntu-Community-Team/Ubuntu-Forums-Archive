---
title: "Can't get nvidia 173 driver to install on 14.04.3 ..."
date: 2016-01-22
forum: Installation &amp; Upgrades
---

### Post by jrancher on 2016-01-22
After installing 14.04.3, my screen booted to black.  I could see the cursor, but nothing else.  After some reading, I started booting by adding nomodeset to the boot options (replacing quiet splash).  After this, it booted fine, but with large graphics (low resolution), and it was very slow (which I assume was also graphics driver related).  I'm installing on a very old machine, a Dell Inspiron 8600 laptop, but it was still comparably slow.

The machine has a GeForce FX 5200 card, which I understand requires Nvidia 173.14.39.  If I go to Additional Drivers under Software Updates, it shows the X.Org driver as selected (I don't know if that means it's active), and it shows the Nvidia 173 driver as selectable.  If I select it, and Apply Changes, it will automatically switch back to the X.Org driver.  It simply won't take.

I then installed Synaptic Package Manager, and selected to install Nvidia-173.  After the system marks all dependent packages to install, it says that one is "broken".  It won't allow the 173 drivers to be installed.

I've searched a ton on ubuntu forums (part of the reason why I got this far).  The closest situation I can find to mine is this thread, in which the poster seemed to have success with almost my exact setup.  But, I can't figure out what he did (I'm on a Linux learning curve right now, so bear with me):

[http://ubuntuforums.org/showthread.php?t=2293379](http://ubuntuforums.org/showthread.php?t=2293379)

Any help would be greatly appreciated.  Thank you.

---

### Post by Madan_Bhandari on 2016-01-22
this is working fine for me on 14.04.03 [http://askubuntu.com/questions/164054/correct-way-to-install-nvidia-173-driver-on-ubuntu-12-04](http://askubuntu.com/questions/164054/correct-way-to-install-nvidia-173-driver-on-ubuntu-12-04)

---

### Post by jrancher on 2016-01-22
> **Madan_Bhandari said:**
> this is working fine for me on 14.04.03 [http://askubuntu.com/questions/164054/correct-way-to-install-nvidia-173-driver-on-ubuntu-12-04](http://askubuntu.com/questions/164054/correct-way-to-install-nvidia-173-driver-on-ubuntu-12-04)

There are actually three separate (proposed) solutions in that thread.

1. The OP seems to have enabled proposed updates, and that worked for him (on 12.04).
2. The next user, also on 12.04, suggested avoiding auto-login and going to command prompt to install manually.
3. The last user has a more involved process of downgrading xorg-xserver.

Which procedure did you follow?

BTW, I just tried the OP's proposed solution, and it didn't work.  But, he was on 12.04.

---

### Post by jrancher on 2016-01-24
Bump.

---

### Post by grahammechanical on 2016-01-24
Have you previously attempted to install a Nvidia driver, any Nvidia driver?

Last year when I was experimenting I installed a Nvidia driver that did not support my Nvidia graphic adapter. And I ended up with Additional Drivers not being willing to deactivate the installed driver and then activate another driver.

If we deactivate a proprietary video driver the OS will automatically revert to using the open source video driver (Nouveau, in the case of Nvidia). This will happen if we purge the proprietary video driver using the terminal. If the remains of an Nvidia driver are clogging up Additional Drivers then run this command.

```
sudo apt-get remove --purge nvidia-*
```

It might take a couple of restarts with opening Additional drivers each time before Additional Drivers starts working again. This command will list the available video drivers for our adapter

```
sudo ubuntu-drivers devices
```

This command will install the current proprietary driver for our video adapter

```
sudo ubuntu-drivers autoinstall
```

The commands take a little time to work.

Regards.

---

### Post by jrancher on 2016-01-25
> **grahammechanical said:**
> Have you previously attempted to install a Nvidia driver, any Nvidia driver?

Last year when I was experimenting I installed a Nvidia driver that did not support my Nvidia graphic adapter. And I ended up with Additional Drivers not being willing to deactivate the installed driver and then activate another driver.

If we deactivate a proprietary video driver the OS will automatically revert to using the open source video driver (Nouveau, in the case of Nvidia). This will happen if we purge the proprietary video driver using the terminal. If the remains of an Nvidia driver are clogging up Additional Drivers then run this command.

```
sudo apt-get remove --purge nvidia-*
```

It might take a couple of restarts with opening Additional drivers each time before Additional Drivers starts working again. This command will list the available video drivers for our adapter

```
sudo ubuntu-drivers devices
```

This command will install the current proprietary driver for our video adapter

```
sudo ubuntu-drivers autoinstall
```

The commands take a little time to work.

Regards.

Sorry about the delay in responding.  I didn't try to install any other Nvidia drivers.

I've only run the command below:

```
sudo ubuntu-drivers devices
```

and I see:

model: NV34M [GeForce FX Go5200 64M]
modalias: pci: xxxxxxx (a bunch of numbers/letters)
vendor: NVIDIA Corporation
driver: nvidia-173 - distro non-free recommended
driver: xserver-xorg-video-nouveau - distro free builtin

---

### Post by jrancher on 2016-01-27
I guess I'm next going to try that third procedure (in the link above) to downgrade xorg-xserver, unless someone chimes in today.

---

### Post by Bashing-om on 2016-01-27
jrancher; Hello:

Option3 should workie great, last long time.
May I suggest that you clean up from any other attempts to install a driver:
```

sudo apt-get remove --purge nvidia*

```
And allow the system to work and install that recommended proprietary driver:
```

sudo apt update
sudo apt upgrade
sudo ubuntu-drivers autoinstall

```

[INDENT][INDENT]I expect
[INDENT][INDENT][INDENT]all there is to it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jrancher on 2016-01-27
> **Bashing-om said:**
> jrancher; Hello:

Option3 should workie great, last long time.
May I suggest that you clean up from any other attempts to install a driver:
```

sudo apt-get remove --purge nvidia*

```
And allow the system to work and install that recommended proprietary driver:
```

sudo apt update
sudo apt upgrade
sudo ubuntu-drivers autoinstall

```
[INDENT][INDENT]I expect[INDENT][INDENT][INDENT]all there is to it
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


I ran the purge command.  It found no installed versions of nvidia drivers.

Ran the update.  It seemed mostly successful, but said something about a few packages not having matching hashes, so it will use "old files".

Running upgrade right now (at 55%).  Taking a while.

I will then run the autoinstall.

So after I do all that, are you saying to proceed with the downgrade of xorg, or is possible that your commands will do the trick?

Thanks.

---

### Post by jrancher on 2016-01-27
OK, I just ran the "sudo ubuntu-drivers autoinstall" and saw this failure message (I've seen this before):

Some packages could not be installed.  This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of the Incoming.
The following information may help to resolve the situation:

[I]The following packages have unmet dependencies:
 nvidia-173 : Depends: xorg-video-abi-11 but it is not installable or
                                xorg-video-abi-12 but it is not installable or
                                xorg-video-abi-13 but it is not installable or
                                xorg-video-abi-14 but it is not installable or
                                xorg-video-abi-15
E: Unable to correct problems, you have held broken packages.
[/I]
Arrg.

---

### Post by Bashing-om on 2016-01-27
jrancher; Well ..

Running 14.04.3 you should still have support for the 173 series driver.
per:
[http://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releases](http://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releases)

ubuntu release 14.04.3 is running version:
```

sysop@1404mini:~$ X -version 
X.Org X Server 1.15.1 ##<-The Version ##
Release Date: 2014-04-13
X Protocol Version 11, Revision 0
<snip>

```
for the X.Org xserver version 

All this said . I would not install a thing until the system is fully completely updated.
Let's take care of that :
> 
Ran the update. It seemed mostly successful, but said something about a few packages not having matching hashes,

Show us the complete output from:
```

sudo apt update
sudo apt upgrade

```
Place these between code tags - promotes and maintains readability .
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

We get the package manager in a happy state, we then can continue .
---------------------------------
addendum :
> 
xorg-video-abi-12 but it is not installable or

I am aware there was a bug in precise for this error. Let my check and see if the situation persist to this time.

[INDENT][INDENT]now a work in progress
[/INDENT][/INDENT]

---

### Post by jrancher on 2016-01-27
> **Bashing-om said:**
> jrancher; Well ..

Running 14.04.3 you should still have support for the 173 series driver.
per:
[http://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releases](http://nvidia.custhelp.com/app/answers/detail/a_id/3142/~/support-timeframes-for-unix-legacy-gpu-releases)

ubuntu release 14.04.3 is running version:
```

sysop@1404mini:~$ X -version 
X.Org X Server 1.15.1 ##<-The Version ##
Release Date: 2014-04-13
X Protocol Version 11, Revision 0
<snip>

```
for the X.Org xserver version 

All this said . I would not install a thing until the system is fully completely updated.
Let's take care of that :

Show us the complete output from:
```

sudo apt update
sudo apt upgrade

```
Place these between code tags - promotes and maintains readability .
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

We get the package manager in a happy state, we then can continue .
---------------------------------
addendum :

I am aware there was a bug in precise for this error. Let my check and see if the situation persist to this time.
[INDENT][INDENT]now a work in progress
[/INDENT]
[/INDENT]


Ok, I'm starting from scratch, so we are all on the same page.  I'm going to reinstall 14.04.3, and then run your commands (and get output directed to file).  I'll report back when I'm done with the update, along with all the output.

---

### Post by Bashing-om on 2016-01-27
jrancher;  Hey !

does this apply to your situation . A graphic's driver PPA ?

[https://answers.launchpad.net/ubuntu/+question/248984](https://answers.launchpad.net/ubuntu/+question/248984)
> 
could not install the package nvidia-331 due to missing dependencies to xorg-video-abi-11 | xorg-video-abi-12 | xorg-video-abi-13 | xorg-video-abi-14.
solution:
Deleting the PPA that the Cuda installer put in /etc/apt/sources.list.d/ and updating the package manager (sudo apt-get update) solved the problem.

----------------
Hey now, it could be

I will add to this post by edits as/of I find more .

---

### Post by jrancher on 2016-01-27
I saw this thread too.  It seems very similar to my situation.  I'm currently upgrading the new install ...

[https://elementaryforums.com/index.php?threads/howto-install-latest-nvidia-driver-on-linux-without-getting-black-screen.7/](https://elementaryforums.com/index.php?threads/howto-install-latest-nvidia-driver-on-linux-without-getting-black-screen.7/)

---

### Post by jrancher on 2016-01-27
This is the exact procedure used to install and update.  I'm probably listing far too much detail, but I want to make sure it's not something simple.


Booted from thumb drive

Selected "try umbunto", hit [Tab] to edit boot options:
	* Added "nomodeset" before "splash quiet" (if I don't do this, the computer will boot to black with white mouse cursor)
	* added "forcepae" because Ubuntu doesn't initially id my CPU as capable of PAE

Ubuntu boots from thumb drive

I run "Install 14.04.3 LTS" from the Desktop, and proceed with the default install (I do not select "Download updates while installing" or "Install this third-party software")

I select "Erase disk and install Ubuntu" (full wipe and install on SSD)

After install, reboot on SSD, ensuring "nomodeset" and "forcepae" are still in the boot options

Then go to linux text command window and type:

```
sudo apt-get remove --purge nvidia-* | tee log1.txt
```

No nvidia drivers are detected or removed.

```
sudo apt update | tee log2.txt
```

Update command appears successfully processed.

```
sudo apt upgrade | tee log3.txt
```

I believe I saw a few errors, something about a broken installation or something.  The output is about a mile long.  How do you want me to post it?  Is there a file generated with only the errors?

---

### Post by Bashing-om on 2016-01-27
jrancher; Well ...

pae cast things in a different light.
I have to question that you set the 'forcepae' parameter correctly as per:
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)
It should be set twice .

Mind you. I know little about pae, but we can keep trying till something gives.

[INDENT][INDENT]if a 1st you do not succeed
[/INDENT][/INDENT]

---

### Post by jrancher on 2016-01-27
> **Bashing-om said:**
> jrancher; Well ...

pae cast things in a different light.
I have to question that you set the 'forcepae' parameter correctly as per:
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)
It should be set twice .

Mind you. I know little about pae, but we can keep trying till something gives.
[INDENT][INDENT]if a 1st you do not succeed[
/INDENT][/INDENT]


I saw that thread several days ago.  From this excerpt, I interpret that 14.04.3 (non-server) does not need to be set twice (I bolded and underlined):

"[COLOR=#333333][FONT=Ubuntu]The "forcepae" option must be entered [/FONT][/COLOR]**twice**[COLOR=#333333][FONT=Ubuntu], before and after the delimiter "[/FONT][/COLOR]**-- **[COLOR=#333333][FONT=Ubuntu]", so that it is applied to both the kernel on the ISO [/FONT][/COLOR]**and**[COLOR=#333333][FONT=Ubuntu] the kernel on the system after installation. This is a change from older installs where only one parameter was sufficient. _**The change applies to Ubuntu Server 14.04.2, 15.04 and later**_ (although it will do no harm to use it on early releases)"

[/FONT][/COLOR]

---

### Post by Bashing-om on 2016-01-28
jrancher; Welp;


You say:
> 
it booted fine, but with large graphics (low resolution), and it was very slow (which I assume was also graphics driver related). I'm installing on a very old machine, a Dell Inspiron 8600 laptop, but it was still comparably slow.


How about we backup and reqroup, download (l)ubuntu:
Lubuntu is a faster, more lightweight and energy saving variant of Ubuntu using LXDE, the Lightweight X11 Desktop Environment. It is targeted at "normal" PC and laptop users running on low-spec hardware.
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)
And try again.

Remember to verify with md5sum the download integrity and also
verify the burn ( boot option check disk for defects ).

What results when booting lubuntu in the "try ubuntu" mode with 2 forcepae boot options enabled ?
I do not expect that "nomodeset" to be required, but we can play about in the "try ubuntu" mode and see what it will take to boot from the liveDVD to the GUI .

I too had an old system with a sempron processor and Nvidia graphics; lubuntu - ubuntu was unbearably slow -  and nvidia-173 ran well on it . ( motherboard bit the dust, and the box was replaced) 

[INDENT][INDENT]surely. we can do that
[/INDENT][/INDENT]

---

