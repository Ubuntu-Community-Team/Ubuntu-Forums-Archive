---
title: "Argh arghh arghh !! Sagem modem !"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by its_jon on 2007-05-08
Oh woe

Oh deary me...

bugger. :confused: 

Installed the latest ubuntu and its not looking good.

I have a disabled modem plus display problems. In my attempts to fix both issues I think I may have made things worse..... Is there any way to reset Ubuntu or is it best to reinstall hoping things will get better ?

I have the Sagem fast 800 broadband modem. It would be great to find a folder containing everything I need and more importantly instructions on how to use all the packs, drivers and stuff as I WONT be able to view this forum when im trying to get up and running.

Please help someone...... make me a rescue pack with an instruction file included... Im very new to Linux but keep trying it out each year with very similar issues.

thanks.

---

### Post by christhemonkey on 2007-05-08
If you are running feisty (or edgy) then when you plug in the modem it should already have the ueagle-atm driver loading all that is needed is the firmware.

To check the driver is loaded, after plugging in your modem, type this;
```
lsmod | grep ueagle-atm 
```
Also check the output of:
```
dmesg | tail 
```

To get the firmware all you need to do is get this file from here: [http://eagle-usb.org/ueagle-atm/non-free/ueagle-data-1.1.tar.gz](http://eagle-usb.org/ueagle-atm/non-free/ueagle-data-1.1.tar.gz)

Then extract it on your pc and put it in the correct folder:
```
tar -xvzf ueagle-data-1.1.tar.gz 
sudo mkdir /lib/firmware/ueagle-atm
cd  ueagle-data-1.1/
sudo cp -a * /lib/firmware/ueagle-atm
```

(if your using edgy you need to stop a conflicting driver being loaded:```
sudo rmmod eagle-usb 
sudo rm /lib/modules/`uname -r`/kernel/drivers/usb/net/eagle/eagle-usb.ko
```)

Then edit the file for the connection this /etc/ppp/peers/ueagle-atm
```
gksudo gedit /etc/ppp/peers/ueagle-atm 
```
And put this in it:
> user "<your username>"
plugin pppoatm.so <VP>.<VC>
noipdefault
usepeerdns
defaultroute
persist
noauth

Where yourusername is obviously [email]foo@what-ever-your-real-login-name-is.com[/email]
And <VP>.<VC> are the VP VC numbers which can be obtained from here:
(for tiscali this is 0.38)

Then you just need to put in your password and username (again) into the files /etc/ppp/pap-secrets and /etc/ppp/chap-secrets:
```
gksudo gedit /etc/ppp/chap-secrets 
```
And make it look like this:
[QUOTE]"<your username>"  "*"  "<your password>"  "*"[/CODE] Dont forget the "*" they are important!

Then just type ```
pon ueagle-atm
``` And your connection should be launched.

Let us know if there are any problems.

See here: [https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm](https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm)

---

### Post by its_jon on 2007-05-08
whats edgy ?.... Ive got the latest desktop ubuntu.... 7.something.... sorry can't check at the moment as im obviously infront of a microsoft desktop at the moment.

I know this is basic stuff but im running firefox on windows.... how do I save this forum thread into a complete local copy so I dont have to cut and past all the info into a text file then onto a disk then boot into linux etc etc....

thanks....

Im sure I did some of these stages but was not allowed to overright some of the files even though I have the root password.... again its a bit of an ioncovenience have to boot between drives everytime I need to check a step....

Im not bieng lazy... I find it difficult enough to understant the instructions without having to frformat them to transfer between OS....

any chance of a info pack with everything included ?

cheers

---

### Post by christhemonkey on 2007-05-08
Feisty and edgy being the relase names for ubuntu version.
7.04 being Feisty, which you have.

On firefox on windows go, file > Save page as, then save it to a usbdisk or something.
You could always print yourself a copy.

As for the root password issue, on ubuntu by default, there is no root acount, so when it asks for a password insert the password of the first user (the one you create when installing).

An info pack im not sure how much clearer i can be, that howto link i gave you in my first post says in as many words how to install your modem. (bear in mind ur using feisty so only follow those instructions)

---

### Post by its_jon on 2007-05-08
thanks.... will keep trying

---

### Post by its_jon on 2007-05-09
Looks like all the software is in place........ I have the eagle stuff in a firmware folder in the lib section of the file system which is as it should be I think.

I copied the contents of the terminal screen and pasted it into a text file which I saved onto the linux desktop.....I was going to copy it onto the windows partition but was met with a permissions error....OK I thought, thats not a bad thing so I tried to burn the text file onto a CD... I get the same permissions error..... I then see if its possible to move the text file into the linux file system.... same problem.....I dont have permission !......why ?.... I logged in with my password on boot....and to the best of my knowledge its the only password I have provided ???? im puzzled.

The reason why I wanted the text was to paste it onto this forum as I think im half way there ....

help :confused:

---

### Post by christhemonkey on 2007-05-09
Ubuntu doesnt currently have the ability to write to ntfs (the main window filesystem) installed by default.
Not sure why there was an error trying to burn the cd, do you have a usb stick you could use?
I feel bad for you burning so many cd's with just text files on them!

As for saving it to the linux file system, the only place an unpriviliged (ie normal) user can save stuff is in there /home/USRENAME/ folder. This is like the 'my documents' on windows. Try saving it there.

---

### Post by its_jon on 2007-05-09
Managed to get this far.....

Does this mean everythings working ?

If not then it must be my connection details added incorrectly. ?

SIDE NOTE: is it possible to keep a CDR open so you can add additional data to it ? ..... I used the CD creation app in Ubuntu to copy this over and its sealed the disk so I cant write anything more to it..... surely there is a option somewhere I missed ?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=32187&stc=1&d=1178753009[/IMG]

---

### Post by its_jon on 2007-05-09
Ok.... so I looked at the help file in ubuntu...

Checked the instructions for ADSL....

I used some sort or automated detection tool which detected a device Eth0 or something but informed me that some other driver may be using it  ???? or something ??

Then below this in the help file, out of all the modems in the world its pointed out that the Sagem 800 is a nasty piece of work and that its far too difficult to explain how to get it working.....which is not very helpful to me.....especially when a link is also provided to a further help relative section ...... ONLINE !!!!! :mad: 

I understand that its a code protection thing...... I also understand that it is possible to get it working.......however... I do feel that some sort of specific help tool could be erm....helpful.

Maybe I have screwed up the connection details ???? ive entered them in so many different ways now via the terminal thingy Im worried they are not in the correct code style for the computer to read properly.

:confused: :confused: :confused:

should I reinstall ?

---

### Post by its_jon on 2007-05-10
OK.... so ive reinstalled Ubuntu.

This time I checked thetransfer windows info button....thinking it may help to configure my connection details...diddnt do that but I do have my XP wallpaper on Ubuntu so something must have worked.

Anyway.... My modem now has two lights on it and when I type the 'check modem' code you suggest it comes back with amongst other things... modem operational.....

I assume my probalem has to be the connection details...

Could you maybe elaborate on the connection details format a bit more please, for example on thesecrets section some stuff is already there seperated by hash# ?? do I remove this or enter my details below it ? ....

thanks.

---

### Post by its_jon on 2007-05-10
[SIZE="5"]BIG SMILES[/SIZE]

Got it working !!!!!

Thanks for the help........

I would like to offer my feedback as a newb attempting to configure this **** of a modem.

Firstly....... 

1) Get the user to enable root control of the file system
2) Get the user to place the driver files in the lib/firmware folder via drag and drop.
3) Get the user to create the eagle folder without using a terminal
4) Get the user to extract the contents of the archive into the folder he has just created NOT using a terminal window.
5) Be very specific about connection details

Lastly it would be great if all these stages were spapshot into a html page package that can be dowloaded to your windows partition.... In fact it would be a great idea to have a large modems help file  that can be downloaded as well as the iso to be left on the users XP desktop just in case of this event.....that way your Ubuntu connection help files can point to the help files on the windows partition. 

anyway.... thanks again.......

got to get my graphics driver working now :)

---

