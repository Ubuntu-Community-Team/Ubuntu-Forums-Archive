---
title: "How to install .bin files"
date: 2010-04-16
forum: Installation &amp; Upgrades
---

### Post by rubled on 2010-04-16
Friends,
Please help me in installing *.bin files in Ubuntu. Im new to Linux.

---

### Post by quadproc on 2010-04-16
> **rubled said:**
> Friends,
Please help me in installing *.bin files in Ubuntu. Im new to Linux.
Probably some of could help but we would need to know more information such as which version of Ubuntu, do you have a network connection, and similar things.

In the world of Unix and Linux we do not usually deal with .bin files; those are usually associated with Microsoft.  Are you wanting to use Microsoft programs on Ubuntu?  If so, then you will need to install some package which allows you to run software intended for Microsoft Windows.

If the software that you wish to install is intended for Ubuntu then the Ubuntu utility named Synaptic is a reasonable tool.  You can also use command line tools such as apt-get but those tools are more work than Synaptic.

You can learn more about the system by using one of several search tools.  Google works well; the Help button at the top of your browser's window may be useful; the "man" command is helpful; the "info" command is also helpful.  You might start by typing into a terminal window ```
man man
```.

Hope this helps, and welcome!

quadproc

---

### Post by jaco223 on 2010-04-16
> **rubled said:**
> Friends,
Please help me in installing *.bin files in Ubuntu. Im new to Linux.

If you're trying to run a windows program or game you might to install wine.
It's a windows emulator.

Open a terminal and type:

```
sudo apt-get install wine
```



What are you trying to run or install exactly?


Jaco

---

### Post by wojox on 2010-04-16
This how you run a .bin file:

```
cd /path/to/file/
```

```
chmod +x file.bin
```

```
./file.bin
```

You may need to add sudo if it needs root privledges.

---

### Post by rubled on 2010-04-17
Good Morning
I tried the commands WOJOX has given and it helped me to install the program. 
but the program crashes. Please help.
attaced is the crash log.

QuadProc,
 I was always a MS system user. Now my efforts are more to learn Ubuntu.
Im using ver 9.1 and i m trying to install googleearth and the version for ubuntu/debeain.
also i have other issues which could be something very silly for you all experts. but lets resolve the issues one by one.

Jaco223
I have wine installed but i did not find it stable. yes i can  install windows file but things rarely works in wine and im going back to windows envirnment agin with wine. so let me try stuff straight with linux.

Thanks all for the  help and suggestions

---

### Post by uRock on 2010-04-17
> **rubled said:**
> Friends,
Please help me in installing *.bin files in Ubuntu. Im new to Linux.

Put the .bin in your home folder, then run the following commands in a terminal to install it. ```
chmod +x nameof.bin
``````
./nameof.bin
``` You will be asked in the dialog for the root password to start the install.

Cheers,
Ronnie

---

### Post by uRock on 2010-04-17
I didn't realise till now that you are trying to install Google Earth. Right click the .bin, then click open with, then click the Use custom command thingy near the bottom and type sh in the window and click enter.

---

### Post by tekkidd on 2010-04-17
Open up the terminal and navigate to the file location 
then 
```
chmod a+x <filename>
```

then 

```
./<filename>
```

---

### Post by rubled on 2010-04-17
Thanks buddy it helped but please see the attached crash log. googleearth doent start. it crashes

> **uRock said:**
> I didn't realise till now that you are trying to install Google Earth. Right click the .bin, then click open with, then click the Use custom command thingy near the bottom and type sh in the window and click enter.

---

### Post by rubled on 2010-04-17
Im also having some security issues ... i dont know how it happened. It doent allow me to change my password and also im not a ble to acces root folder. can some one help. If possible can someone take a remote session to my pc and do all the fix so that i can see and learn how to fix this issues.
Reagrds,
Ruble
my skype ID ruble.daniel alternativily if someone is available in UAE ( dubai) please geive me a miss call on my mobile 00971505411047 and help me please

---

### Post by IndyGunFreak on 2010-04-17
> **rubled said:**
> Im also having some security issues ... i dont know how it happened. It doent allow me to change my password and also im not a ble to acces root folder. can some one help. If possible can someone take a remote session to my pc and do all the fix so that i can see and learn how to fix this issues.
Reagrds,
Ruble
my skype ID ruble.daniel alternativily if someone is available in UAE ( dubai) please geive me a miss call on my mobile 00971505411047 and help me please

So it won't let you change your user password?  Do you know your root password?  Your "root" password(depending on what instructions you've followed) should be the same as your user password.

Ubuntu doesn't have a root account per se.. .What exactly are you trying to do?

---

### Post by rubled on 2010-04-17
Ken,
Im so sorry i know you tried to reach me on skype to help me. if you fre now please call again or please give me 30 mintues..Thanks once again for your response.
Ruble

> **rubled said:**
> Im also having some security issues ... i dont know how it happened. It doent allow me to change my password and also im not a ble to acces root folder. can some one help. If possible can someone take a remote session to my pc and do all the fix so that i can see and learn how to fix this issues.
Reagrds,
Ruble
my skype ID ruble.daniel alternativily if someone is available in UAE ( dubai) please geive me a miss call on my mobile 00971505411047 and help me please

---

### Post by rubled on 2010-04-17
Ken
yes i know my root password.  and my ID has admin right but it doent allow me to chnage my password and also i cannot access root folder. due to this acces restriction which got applied without my knowledge is stopping me from installing applications also as it say access denyed for few system folders. I dont know the real technical terms in Linux to explain more. I would appreciate if someone could take a remote session to find out the issues.
Regards,
Ruble

> **IndyGUnFreak said:**
> So it won't let you change your user password?  Do you know your root password?  Your "root" password(depending on what instructions you've followed) should be the same as your user password.

Ubuntu doesn't have a root account per se.. .What exactly are you trying to do?

---

### Post by rubled on 2010-04-17
Friends,
I wll be back in 20 minutes.. Thanks all for helping me

---

### Post by lisati on 2010-04-17
Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

