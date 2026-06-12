---
title: "After apt-get autoremove Ubuntu 11.10 wont boot"
date: 2011-12-28
forum: Installation &amp; Upgrades
---

### Post by drackololord on 2011-12-28
I am running an Acer Aspire X1200  [http://support.acer.com/acerpanam/desktop/0000/Acer/AspireX1200/AspireX1200sp2.shtml](http://support.acer.com/acerpanam/desktop/0000/Acer/AspireX1200/AspireX1200sp2.shtml)

with an only Operative system (No windows or another Distro) that is Ubuntu 11..10 64 bits Edition, the partition of it its Sda4 and the Sda1 its the linux-swap


Hello everyone yesterday i was having a little troubleshoot installing new virtual box version, did not uninstall it, and searching i find this command, already have been run it and nothing bad happens, its this 

```
sudo apt-get autoremove
```after it i just saw something about gnome, by by good luck id take a screenshot, lucky me, and it is this 

[http://www.flickr.com/photos/66277877@N08/6586104543/in/photostream](http://www.flickr.com/photos/66277877@N08/6586104543/in/photostream)

it was just 100 MB, don't remember doing anything else, turn it off and then, BLACK SCREEN :(:(:( :cry:
i dont see nothing, actually it gets black freezed screen, it doesnt beep or send me another type of command prompt

tried everything and nothing works, already found this

[askubuntu.com/questions/62640/after-apt-get-autoremove-missing-operating-system]("http://askubuntu.com/questions/62640/after-apt-get-autoremove-missing-operating-system")
everything as he says happens to me except it doesnt show anymore this text,

```
Missing Operating System.
```tried the solution he gave with my Live Cd Ubuntu 11.10 64 bits

```
sudo mount /dev/sda2 /mnt
``````
sudo grub-install --root-directory=/mnt /dev/sda 
```ans it shows me this

_[http://www.flickr.com/photos/66277877@N08/6589997027/in/photostream](http://www.flickr.com/photos/66277877@N08/6589997027/in/photostream)_

already try to repair broken packages with my cd using recovery mode pressing SHIFT or Esc and nothing, it shows me this, and gets freezed at this --Recovery Menu (limited read-only menu)--
try to remount and gets freezed so I cant repair brocken packages

[http://comments.gmane.org/gmane.linux.ubuntu.devel/34370](http://comments.gmane.org/gmane.linux.ubuntu.devel/34370)

what can i do

thanks you for anticipated

:confused:

---

### Post by hsoulen on 2011-12-28
Hi drackololord.

Couple of quick questions to get started:

[LIST=1]
[*]What version of Ubuntu are you running?
[*]Are there any other Operating Systems on the machine that load through Grub?
[*]What do you see when you boot? Do you get any kind of command prompt? (I cannot see your second Flikr image)
[/LIST]

I am asking as it appears that you removed gdm which could be an issue.

Hank

---

### Post by drackololord on 2011-12-28
Finished editing hosulen!

-Ubuntu 11.10 64 bits
-This is my only Os (no windows)
-I dont see any prompt, just freezes in black screen and nothing, cpu light blinks and then nothing

thanks hsoulen!

---

### Post by drackololord on 2011-12-28
:guitar:Lol, lol, id solved this by myself, did not need anyone help, instead, no one did!

ROFTL

ROFTL!!!

It was really easy, so easy, as I was saying, it happened before i did

```
sudo apt-get autoremove
```

[http://www.flickr.com/photos/66277877@N08/6586104543/in/photostream](http://www.flickr.com/photos/66277877@N08/6586104543/in/photostream)

and how lucky I was for taking a screen shot of it, because I saw something about gnome, and some system utilities, after trying a lot of hints and randoms code, fixing MBR or grub (which wasn't) i start in normal mode, pressed CTRL + ALT + F1 or F2 I entered into COnsole Mode, i did logon with the Administrator Account, typed this

```
 sudo apt-get install gnome 
```

asked me for using 140 Mb, I say yes, installed (using my Internet connection) and LOLOLOL, restarted, and I was able to see my login windows, pffff

I was going to reformat, and that is so boorringgggg to me,

instead of this its saying me that [COLOR=#666][/COLOR] "could not update iceauthority file home user .iceauthority" but that is another problem, id used my limited account, and I will fix it later, on my free time, 

thanks anyway for not helping me,

the answer was inside me, after all 145 persons cant be better than me, hahahahahha

so funny 

bye dudes

---

### Post by hsoulen on 2011-12-29
Glad you got it fixed, but with that said...

Nice attitude. :confused:

I was trying to help you, you'll note that my comment was that it looked like you removed gdm... Hence you removed gnome. I asked you the other questions in anticipation of assisting you.

FYI I will never reply to one of your queries again since you obviously do not appreciate anyone providing you with free support.

Best of luck on your own.

Hank

---

### Post by drackololord on 2011-12-29
Of course I do appreciate your help, hosoulen, JUST YOUR HELP, not the others, instead i did not read everything of your answer, just the 3 first of them, i am really thankfully, specially with the one who answer me, like YOU

You must be ANGRY AND UPSET, anyway, I did have to found myself my solution, and as I told before, I should not post anything, the solution was sooooooooo easy, have to look to my own screenshots, anyway, you know more than me, really, 

and I am angry with the people who only watch and dont participate, more than 100 to be exactly,

thanks again, and good luck

dont get it personally

---

