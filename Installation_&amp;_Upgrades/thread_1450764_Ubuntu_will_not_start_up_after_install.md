---
title: "Ubuntu will not start up after install"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by bnrauch on 2010-04-09
I am a Linux newbie, I installed version 9.10 32 bit on my new MSi a6200 lap top using wubi.
I installed it with-in windows. After restarting and selecting Ubuntu it shows the message finishing install then the screen gos  blank. I can here the hard drive spinning but nothing comes up on the display. Has anyone else experinced this same issue if so what is the fix. Please be detailed as I am fairly new to this.

---

### Post by _BIG_ on 2010-04-26
> **bnrauch said:**
> I am a Linux newbie, I installed version 9.10 32 bit on my new MSi a6200 lap top using wubi.
I installed it with-in windows. After restarting and selecting Ubuntu it shows the message finishing install then the screen gos  blank. I can here the hard drive spinning but nothing comes up on the display. Has anyone else experinced this same issue if so what is the fix. Please be detailed as I am fairly new to this.

im having the same exact problem with the same model laptop

msi a6200 = msi cr620

but msi doesnt have anything for unbuntu/linux help or drivers that i can tell

i just did this same install on my desktop and worked fine.  if you let it sit on the blank screen right after install it finishes the install just like my desktop did BUT you cant see anything on the laptop.  it restarts then back to the blank screen where i imagine the login is sitting we just cant see it


edit:

lol for the hell of it i hit enter and put in my password, hit enter again and i heard the load up sound....but still no visual

---

### Post by P4man on 2010-04-26
edit: disregard,  seeing you can log in, its nothing with grub.

---

### Post by P4man on 2010-04-26
> **_BIG_ said:**
> 
lol for the hell of it i hit enter and put in my password, hit enter again and i heard the load up sound....but still no visual

Try this: press control alt F1. Do you get a full screen "dos" screen? If so, press control alt F7. Do you get a GUI now ? 

Also  is it possible the screen is working but no backlight? Try looking very hard if you cant see something on the screen in bright light.

---

### Post by _BIG_ on 2010-04-26
> **P4man said:**
> Try this: press control alt F1. Do you get a full screen "dos" screen? If so, press control alt F7. Do you get a GUI now ? 

Also  is it possible the screen is working but no backlight? Try looking very hard if you cant see something on the screen in bright light.

after ive logged in right?
i can tell i logged in from the startup sound
control + alt + F1 does nothing for me that i can tell
controla + alt + F7 does nothing for me that i can tell

there is definatley backlighting the screen is glowing but black

same thing happens in recovery mode as well

---

### Post by dannyboy79 on 2010-04-26
sounds like a video card driver problem. try this
after the computer is booted up fully.
then hit ctrl-alt-F1, you should be brought to a dos looking screen asking you for your username.
enter the username you created during install, enter password you chose. once in here issue this command
```
sudo service gdm stop
```
also we need to find out what grpahics card you ahve. issue 
```
lspci > lspci.log
```
and tell us what the output is. easiest way instead of writing it all down is this.
```
sudo aptitude install pastebinit
```
enter your password.
once it's done installing issue this
```
pastebinit lspci.log
```
that should spit back a link to  a pastebin website where that file just for uploaded. 
tell us what that link is. good luck

---

### Post by _BIG_ on 2010-04-26
danny - when i hit control alt f1 i get no change in appearance.  im sure its there but i cant see anything

i also tried to boot from the cd "try ubuntu without changing anything on your computer" and it gives me the same blank screen

---

### Post by P4man on 2010-04-26
Can you try booting the live cd in safe graphics mode?

[IMG]https://help.ubuntu.com/community/BootOptions?action=AttachFile&do=get&target=bootf4.png[/IMG]

---

### Post by dannyboy79 on 2010-04-26
chiggidy check this out YO:
[http://ubuntuforums.org/showthread.php?t=1317951](http://ubuntuforums.org/showthread.php?t=1317951)

should solve your problem as the MSI has an intel graphics card

---

### Post by _BIG_ on 2010-04-26
> **P4man said:**
> Can you try booting the live cd in safe graphics mode?

[IMG]https://help.ubuntu.com/community/BootOptions?action=AttachFile&do=get&target=bootf4.png[/IMG]

no i cant :\.....wait i just did...it went blank for awhile then squiggly after 5 mins and all of a sudden the desktop showed up

danny - 
thise helped get the little white ubuntu logo in the middle of the screen but then back to blank screen again
> **mutrax said:**
> hehe... been there to.

Just add i915.modeset=0 to your kernel parameters. 

If you are using karmic, this is situated in /boot/grub/gru.cfg.

I changed mine like this....
```

linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=74befa82-a138-491d-9188-84b1888aed00 ro   quiet splash*** i915.modeset=0***
```




as of right now i am seeing my desktop on the livecd ...not sure if its safe graphics mode or not tho...

---

### Post by _BIG_ on 2010-04-26
i dont know if this will help but my laptop has an intel i5 430m with intel gma hd which is on the cpu i believe.  might help you guys help me lol

---

### Post by _BIG_ on 2010-04-26
fixed the problem magically!

1. highlight ubuntu recovery mode and press e
2. look for the line that ends with the word SINGLE after it type in nomodeset
3. ctrl +x
4 choose update bad packages i think thats what it said)
5. let it run and till its done then reboot

basically upgraded everything like it would when you first get into the desktop and do the updates


hope this helps

---

### Post by dannyboy79 on 2010-04-27
> **_BIG_ said:**
> fixed the problem magically!

1. highlight ubuntu recovery mode and press e
2. look for the line that ends with the word SINGLE after it type in nomodeset
3. ctrl +x
4 choose update bad packages i think thats what it said)
5. let it run and till its done then reboot

basically upgraded everything like it would when you first get into the desktop and do the updates


hope this helps
mark it solved please. glad you got it sorted out

---

### Post by svenaustx on 2011-07-12
> **dannyboy79 said:**
> sounds like a video card driver problem. try this
after the computer is booted up fully.
then hit ctrl-alt-F1, you should be brought to a dos looking screen asking you for your username.
enter the username you created during install, enter password you chose. once in here issue this command
```
sudo service gdm stop
```
also we need to find out what grpahics card you ahve. issue 
```
lspci > lspci.log
```
and tell us what the output is. easiest way instead of writing it all down is this.
```
sudo aptitude install pastebinit
```
enter your password.
once it's done installing issue this
```
pastebinit lspci.log
```
that should spit back a link to  a pastebin website where that file just for uploaded. 
tell us what that link is. good luck

____________________________
This long later, have same problem, directing this to dannyboy79, went through this procedure, and got a PasteBin ...

---

