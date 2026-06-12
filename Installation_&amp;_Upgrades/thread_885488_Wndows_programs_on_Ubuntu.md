---
title: "Wndows programs on Ubuntu ??"
date: 2008-08-10
forum: Installation &amp; Upgrades
---

### Post by Armen818 on 2008-08-10
is there a way to install windows programs on ubuntu???
there are couple i need, if it does work ill just give up on windows and use Ubuntu as my main OS



ty

---

### Post by lisati on 2008-08-10
Windows programs don't usually work on Ubuntu without help - your best bet is to either find a Linux equivalent, or to use "Wine"

EDIT: Have a look [here]("https://help.ubuntu.com/community/SoftwareFromOtherOperatingSystems")

---

### Post by demon_hunter on 2008-08-10
yes. there is .its called wine ,but it depends which programs you want.try and google it.put in,program name install on ubuntu.
hope i help:)

---

### Post by Keith Hedger on 2008-08-10
u can also use a virtual machine vmware or virtualbox are the most common but u do need a windows install disk as well

---

### Post by geraldvillorente on 2008-08-10
in my case i need some windows applications on my ubuntu machine...im using wine and it works very well...to install wine just type "sudo apt-get install wine" on your console..

---

### Post by liquidfunk on 2008-08-10
As people have said, it does generally depend on what programs you want to use. 

 Here is a website that shows how well programs run, and don't run. 

[HTML]http://appdb.winehq.org/[/HTML]

 As for getting Wine:

 Open up a Terminal, which is generally located under Applications - Accessories - Terminal

 Copy and paste this: 

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

 (If you select the code, and Middle-click it into the terminal it saves pressing CTRL + C and CTRL + V).

 Followed by: 

```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
```

 Then:

```
sudo apt-get update
```

```
sudo apt-get install wine
```

 Then once it has installed type 

```
winecfg
```

 Into the terminal.

 That will bring up a box. Click Graphics, and select 

```
 Allow the window manager to decorate the windows
``` 

 and

```
 Allow the window manager to control the windows
```

 Then open up Audio (It takes a few seconds - It hasn't frozen though)

 I tend to click all of the boxes, then under Hardware acceleration put Emulation, then click Driver Emulation,but have a play around.

 Then just double click the programs installer, and use like in Windows.

  If the program opens then just closes, try opening up a Terminal and typing wine and then dragging the shortcut into it.

 So for example: 

```
wine '/home/josh/wow/Wow.exe' 
```

 Is what it would look like. 

 Then post the output onto the forum or onto the Wine forums.

 Enjoy!

---

### Post by Armen818 on 2008-08-10
ty very much guys ill give it a try.
the reason i was asking is that whan i get a macbook pro, i wanna have both OS X and Ubuntu  Not windows on my mac. I might use windows XP for games.
But just a bare bone windowsXP. i don't want to deal with windows problems anymore i'm sick of it. Update after update and it never fixes the problem and than there are the spyware and virus.

---

### Post by liquidfunk on 2008-08-10
If its a Mac you are after, then you can still run Wine on MacOSX. 

 There is also Crossover, and Crossover Games for Mac, that costs a bit, but it's good.

 I'm not sure on how well Ubuntu works out of the box on a Macbook Pro, I've been wanting to Dual-boot my Macbook with some form of Linux for a while.

---

### Post by Armen818 on 2008-08-12
a friend of mine has Ubuntu on his macbook pro and it works fine, with out any problems.

---

### Post by willieboy on 2008-08-12
Crossover is more stable then Wine, but it costs £25 UK  $47 USA.
It is good.

---

### Post by liquidfunk on 2008-08-12
/agree

 Yeah, crossover is good, but I'd rather not spend money on something that does the job for free.

 As the only Windows program I use is WoW, which works amazingly well, I'm not fussed.

 Although, yes, Crossover is good.

---

