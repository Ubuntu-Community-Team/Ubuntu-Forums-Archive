---
title: "Wine Help Please"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by Pioneer5000 on 2007-07-24
Ok my overall goal is to get wc3 running on linux using wine. So i looked around the forums trying to find a way to do this found several topics on it but everyone doesnt work for me. So i decided just to try installing wine forget about wc3 for now. So i used this guide to install it 

Adding the WineHQ APT Repository:

First, open a terminal window. Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Next, add the repository to your system's list of APT sources:

For Ubuntu Feisty (7.04):
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list

and then sudo apt-get update 

ok after doing this i go into Symaptic go to install wine, and a couple of the other stuff thats with it eg. wine-dev , libwine, libwine dev

i install wine by itself first it doesnt it but i dont see it anywhere, i install wine-dev and well and then i try to install libwine and libwine-dev but they give me this error

libwine-dev:
 Depends: wine-dev but it is not going to be installed

libwine:
 Depends: wine but it is not going to be installed

but according to synaptic wine and wine-dev is install but i dont see it anywhere and these other 2 compents cant install cause they arnt installed. 

Also i have winetools installed but it wont run cause i dont have a new enough version of wine install appreantly... well this isnt that important cause once i get the above solved this will be solved or even better can someone give me a proper installation guide that could lead me to wc3 being installed the other one i found on the forums doesnt work for me.. any help would be appreciated. Thanks.

---

### Post by ubuntu.daemon on 2007-07-24
hey man well you might need some other stuff... go to winehq.com bc they have alot more support especially for wc3, i have starcraft& expansion running in my laptop.... i dont know why you added the winehq repository why not just 
```
user@home: sudo apt-get install wine
``` <--- in terminal
 
you didnt need the newest version for wine, just make sure u have universe and multiverse enabled

just try that and see where it gets you

---

### Post by Pioneer5000 on 2007-07-24
Yea ive tried that, then when i try to run wine tools by typing "wt" in the terminal i get this error message back "Winetools cannot run with a Wine Version older then 20050628..." or do i not need wine tools to get wc3 running? and is wine spose to show up some where like in my applications menu or something cause its not there. Ive done both installed wine like you said and how the wineHQ site says but where is it?

---

### Post by Pioneer5000 on 2007-07-24
.............. OMG it worked thats all i need was that one line i didn't even need wine tools!!!!!!!!!!! arg! why were there so many guides saying to get wine tools and all those guides telling you to install all this other crap all you needed was one in of code in the terminal and then you just put the disc in and then double click auto run and thats it.............. i cant believe it..well thanks so much for the help man. I just cant believe how simple it was compared to all the stuff i was trying to do. Thanks. :)

---

### Post by ubuntu.daemon on 2007-07-25
lol yeah wintetools is really not needed, most people here on the forums dont  know about winehq.com  has alot etter info and help for install/configuring wine for games/etc.  Anyways glad you solved your problem though! 
:popcorn:

---

### Post by Pioneer5000 on 2007-08-14
Man, this sucks I decided to reformat my hdd and get rid of windows all together so now i'm running only ubuntu but now after formatting my hdd when i use the user@home: sudo apt-get install wine command to install wine, it installs wine but it doesn't work. Before all I had to do was put that line in terminal and then put game in eg. wc3 and then just double click on the install.exe icon in the folder but now all i get is this for starcraft: "Cannot open /media/cdrom0/install.exe: No application suitable for automatic installation is available for handling this kind of file." Before doing that sudo apt-get win line thing i actually tried a lot of others way of getting it working maybe if was something i did earlier that made it run the first time and not actually the sudo apt-get install wine command. Can someone help me to fix this problem please. Thanks.

---

### Post by Pioneer5000 on 2007-08-14
ive also tried:

```
bob@bob-desktop:~$ cd /media/cdrom0
bob@bob-desktop:/media/cdrom0$ wine setup.exe
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
bob@bob-desktop:/media/cdrom0$ Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side color-index mode DIB copy
fixme:bitblt:X11DRV_ClientSideDIBCopy potential optimization: client-side color-index mode DIB copy
```

it starts up Starcraft set up menu, i type in name and cd key and then i get this error:

"exp1: Error 3: Path no found"

How do i fix this and get Starcraft installed? Help Please.

---

### Post by ubuntu.daemon on 2007-08-14
lol you need to do 
```
user@home: winecfg
```and then you will be able to install, bc that sets up the windows directory.  Oh and i personally have starcraft installed so let me know if you have any other problems. GL
:popcorn:

EDIT: Oh and make a link in the drives tab to you /media/cdrom0

---

### Post by Pioneer5000 on 2007-08-14
bob@bob-desktop:~$ winecfg
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.


then it opens the menu thing. Then what do i do?

---

### Post by Pioneer5000 on 2007-08-14
^ ive tried tahts like 10 times btw

---

### Post by Pioneer5000 on 2007-08-14
ok i uninstalled wine and then reinstalled it
 ```
 sudo apt-get install wine
```
and then i did
```
winecfg
```
and this time it worked properly and made directly etc. i installed the game but when i got to connect to battle.net it stuffs up.. just closes down .. i can play single player and everything perfect although it seems a bit slow.

---

### Post by Pioneer5000 on 2007-08-14
Ok, got it working now finally..... only one problem when in the battle.net screen eg. a channel everything is black and i have to kind o guess where the buttons are etc. i can see messages coming in but almost everything else is black so i kind have to guess how to get into a game, but when in game everything is fine except game feels a bit slow well mouse movement anyway. Yo thanks for the advice.

---

### Post by vexorian on 2007-08-14
tried with opengl? It should be faster and stop those rendering issues

```
 wine ./war3.exe -opengl
```

Also window mode:

```
 wine ./war3.exe -opengl -window
```

also, try the speed up tricks on [http://ubuntuforums.org/showthread.php?t=497332](http://ubuntuforums.org/showthread.php?t=497332) specifically removing the debug output makes it much faster.

I also found that compiz-fusion and WINE are not good friends, btw.

---

### Post by Pioneer5000 on 2007-08-15
^ Thanks for the help man. But i am still getting problem with mostly black screen when im in battle.net screen its weird every where else is perfect. But when i connect to battle.net the background goes black the writing is in white not the normal battle.net font's cant see any buttons or anything. Very hard to nevigate around to join game. But once in game is back to being perfect again. Well besides the slowness. I dont think the opengl command line you gave me works. Thanks though. :)

---

