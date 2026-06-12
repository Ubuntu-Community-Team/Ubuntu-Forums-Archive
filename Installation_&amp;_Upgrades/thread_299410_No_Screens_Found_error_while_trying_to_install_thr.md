---
title: "No Screens Found error while trying to install through Live CD"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by ZoidbergForPresident on 2006-11-14
Everything is in the title...

I have a Dell computer with an ATI X600 card and when I try to "Launch or Install Ubuntu" it loads then I get a strange error screen telling me X couldn't be started...

Tried with other resolutions and with the second launch option (default settings or whatnot)...

Ubuntu is supposed to be directed at human beings so why won't it let me boot it on the Live CD to install it!!!?

---

### Post by ZoidbergForPresident on 2006-11-14
Nobody?

---

### Post by wpshooter on 2006-11-14
Are you using the DESKTOP CD ?

If so, download and try the ALTERNATE CD.

---

### Post by ZoidbergForPresident on 2006-11-14
> **wpshooter said:**
> Are you using the DESKTOP CD ?

If so, download and try the ALTERNATE CD.

A reason for that?

---

### Post by usererror on 2007-01-08
I also have this problem now.  I am downloading the Alternate CD at the moment but pressing CTRL + ALT + F4 took me to a command prompt after the X errors so I can at least use Vi to look at the xorg.conf file...

Jackpot!  From the command prompt I installed the package (xorg-driver-fglrx) that allows me to use the command:

```

aticonfig --initial=dual-head

```

Remove the =dual-head if you don't have dual monitors

it created an xorg.conf file, then i typed startx and now i am in the setup with dual monitors.  PHEW!!!

Once you are in gnome go to System > Administration > Install to start the Ubuntu installation process.

After the install is done, reboot.  I had to reboot by starting a terminal and doing **sudo reboot**

It'll reboot and then of course you've lost your xorg again.  go back to the command prompt, install the fgrlx package like above, re-run aticonfig, and then startx from the command prompt...

I'm doing the 150 updates that are needed so hopefully that fixed all of it...and that the updates DON'T break it. :D  I hope this helps someone!

---

### Post by ZoidbergForPresident on 2007-01-28
I tried again, got to a command-line and altough I had the keyboard set to qwerty (while I have a Belgian azerty) I tried the commands you gave and they're not recognized...

What have I to do, how and where please?

---

### Post by usererror on 2007-01-28
> **ZoidbergForPresident said:**
> 
What have I to do, how and where please?

From the prompt can you do:

```
sudo apt-get install xorg-driver-fglrx
```

?

---

### Post by ZoidbergForPresident on 2007-01-28
> **usererror said:**
> From the prompt can you do:

```
sudo apt-get install xorg-driver-fglrx
```

?

So I type that then?

---

### Post by usererror on 2007-01-28
Yes, if you can install that video driver successfully and then run:

```
aticonfig --initial
```

that should get the video setup correctly.  Once that is complete do a ```
startx
``` and then Run setup from Gnome like you would normally if you didn't have any video problems in the first place. :D

---

### Post by Botunda on 2007-01-28
Alright I think I am having the same issue and I am DL'ing the alternate cd. Until then I can't seem to install the following:

```
sudo apt-get install xorg-driver-fglrx
```

It says that it couldn't resolve 'security.ubuntu.com'


I am hard-wired into the router and it's up. So I guess I need some help.

TIA

---

### Post by usererror on 2007-01-28
Botunda,

Do you have an IP address from your wired router?  do an 'ifconfig' to verify that eth0 has an IP...if it does, try to ping an outside address like [www.google.com](www.google.com).  If you cannot ping out of your network you won't be able to download the apt package. :(

---

### Post by Botunda on 2007-01-28
correct, I am not getting any connection. That is currently what I am attempting. I do an ifconfig and not getting an ip address

---

### Post by usererror on 2007-01-28
> **Botunda said:**
> correct, I am not getting any connection. That is currently what I am attempting. I do an ifconfig and not getting an ip address

hmm, this is not good.  what kind of network card do you have?  my guess is that there isn't driver support for your NIC compiled into the kernel in Edgy that is on the disk you're using.  i'm not sure what the solution would be, maybe put in an older network card?

If you go to a promt and type in 'lspci' is your NIC listed?

---

### Post by Botunda on 2007-01-28
Alright got my card working. I have download packages stated ealier. Now when I startx I get a the login/pass screen and then it hangs.

Then a white box comes up into the top left-hand corner. I saw the meesage the first time. Something about daemon not start correctly. I should have written it down. BUt if I wait for about 3min and then it finishes loading up.

Anyone got an idea why it hangs like that?


TIA

---

### Post by ZoidbergForPresident on 2007-01-29
Ok thx for the heads up, I'll try that.

But my pc should actually have a static ip, where do I put that in command line?

---

### Post by usererror on 2007-01-29
> **ZoidbergForPresident said:**
> Ok thx for the heads up, I'll try that.

But my pc should actually have a static ip, where do I put that in command line?

you do that in the /etc/network/interfaces file.  use VI to edit that file.  is there no way for you to do DHCP for just this one time?

---

### Post by ZoidbergForPresident on 2007-01-29
> **usererror said:**
> you do that in the /etc/network/interfaces file.  use VI to edit that file.  is there no way for you to do DHCP for just this one time?
I guess I could...

So I boot on the live cd... start in command line, type "sudo apt-get install xorg-driver-fglrx"
then "ati..." then startx?

And it should work?

---

### Post by usererror on 2007-01-29
> **ZoidbergForPresident said:**
> I guess I could...

So I boot on the live cd... start in command line, type "sudo apt-get install xorg-driver-fglrx"
then "ati..." then startx?

And it should work?

Yes that *should* work.  It worked for my case.

---

### Post by ZoidbergForPresident on 2007-01-29
> **usererror said:**
> Yes that *should* work.  It worked for my case.
Tried it and when I type the first command, when he tires to connect, I get:

0% Connexion à archive.ubuntu.com (1.0.0.0.) ] _

Then nothing, it just stays as is...

If 1.0.0.0. is the ip of archive then there's a problem

I'm fed up with it, Ubuntu (and Linux in general) is supossed to be easy to install and getting an error of the graphic gui is bad... :(

---

### Post by usererror on 2007-01-29
> **ZoidbergForPresident said:**
> I'm fed up with it, Ubuntu (and Linux in general) is supossed to be easy to install and getting an error of the graphic gui is bad... :(

well, then don't use it.  i hate to say it.  I don't know why has a 1.0.0.0 IP for that archive.  There is probably way to do the text only installer but I don't know what it is.

---

### Post by ZoidbergForPresident on 2007-01-29
> **usererror said:**
> well, then don't use it.  i hate to say it.  I don't know why has a 1.0.0.0 IP for that archive.  There is probably way to do the text only installer but I don't know what it is.

Why there's no problem on a pc with integrated graphics while not having generic display drivers for an ati card?

Not serious...

Well, thanks for the advices anyway!

---

### Post by usererror on 2007-01-29
> **ZoidbergForPresident said:**
> Why there's no problem on a pc with integrated graphics while not having generic display drivers for an ati card?

Not serious...

Well, thanks for the advices anyway!

There is no problem with the onboard graphics because those generally can function with just a basic driver.  Expension Video Cards in PCIe or AGP slots are more 'sophisticated' and require more 'attention' from the OS to function correctly.

---

### Post by Botunda on 2007-01-29
> **usererror said:**
> well, then don't use it.  i hate to say it.  I don't know why has a 1.0.0.0 IP for that archive.  There is probably way to do the text only installer but I don't know what it is.

There must be something in your /etc/network/interface file that is screwy. At least that was it for me. Follow the directions for get the Ethernet 'eth0' up and use DHCP. 

Don't give up and try and have an open mind with these things. If it was easy, everyone would be doing it! :D

---

### Post by usererror on 2007-01-29
> **Botunda said:**
> Don't give up and try and have an open mind with these things. If it was easy, everyone would be doing it! :D

WELL SAID! :D

---

### Post by Chark on 2007-01-30
I seem to be having the same issues with the livecd to install, X can not start and is giving the no screens found, I have a dell e1705 with integrated graphics, (not an ati card)
Mobile Intel 945GM Express (I think)

---

### Post by usererror on 2007-01-30
Now that is intersting.  what happens if you run the script to re-configure X from terminal?  i'm drawing a blank on what it is at the moment.  I'm still a newbie myself. :D

---

### Post by Chark on 2007-01-31
Yep, was able to get it working (after a few tries) with dpkg-reconfigue xserver-xorg

Thanks :D

---

### Post by usererror on 2007-01-31
> **Chark said:**
> Yep, was able to get it working (after a few tries) with dpkg-reconfigue xserver-xorg

Thanks :D

YES!  That was the code.  i couldn't remember it.  awesome!

---

### Post by nibsa1242 on 2007-02-07
This worked for me while installing to my desktop. (w/ ATI X800 XL)

---

### Post by okhascorpio on 2007-02-27
i found work-around for similar problem, i waz having, u might find it kind a weard :biggrin: ... but.. here it iz.. i just unplug data cable of my monitor, untill i hear the starting sound, then i conect data cable again, and everything works fine, .. but have to do same drill every time i restart my pc... :(   if any one can get a hint to real solution.. plz post..

---

