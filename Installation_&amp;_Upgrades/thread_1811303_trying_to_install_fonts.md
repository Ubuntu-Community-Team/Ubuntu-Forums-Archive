---
title: "trying to install fonts"
date: 2011-07-24
forum: Installation &amp; Upgrades
---

### Post by bobk_nyc on 2011-07-24
tts is a real pain. I was trying to install fonts, and the teerminal locked up would do nothing, soI rebotted, and now I get this

bobk@penguin:~$ sudo apt-get install msttcorefonts
[sudo] password for bobk: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

why can't I just copy fonts to a font folder....

---

### Post by coffeecat on 2011-07-24
> **bobk_nyc said:**
> 

why can't I just copy fonts to a font folder....

You can. Create (if it isn't already there) a hidden folder called ".fonts" in your home folder and copy/move any *ttf fonts you want into it. That's it - installed. Even easier - double-click on your *.ttf file and follow the prompt.

You might want to run "sudo dpkg --configure -a" to repair your package manager which is your immediate problem - not installing fonts.

---

### Post by bobk_nyc on 2011-07-24
> **coffeecat said:**
> You can. Create (if it isn't already there) a hidden folder called ".fonts" in your home folder and copy/move any *ttf fonts you want into it. That's it - installed. Even easier - double-click on your *.ttf file and follow the prompt.

You might want to run "sudo dpkg --configure -a" to repair your package manager which is your immediate problem - not installing fonts.


I did that, it asked for pw, and didn't seem to do anything...is that right?

---

### Post by coffeecat on 2011-07-25
> **bobk_nyc said:**
> I did that, it asked for pw, and didn't seem to do anything...is that right?

The seem is right. In the terminal, when you type your password in, it is not echoed back to the screen and nothing appears to be happening. It is. Simply type your password and then press enter and then the terminal will process your command. Also, you may get no message after the command if there is no error to report. With some commands you get plenty of feedback but with some, being returned to the prompt with no output means the command has completed successfully. It can be a bit disconcerting, but you will get feedback if there is an error.

---

### Post by bobk_nyc on 2011-07-25
> **coffeecat said:**
> The seem is right. In the terminal, when you type your password in, it is not echoed back to the screen and nothing appears to be happening. It is. Simply type your password and then press enter and then the terminal will process your command. Also, you may get no message after the command if there is no error to report. With some commands you get plenty of feedback but with some, being returned to the prompt with no output means the command has completed successfully. It can be a bit disconcerting, but you will get feedback if there is an error.

well. I guess, I will just keep this os on a not important machine for now, seems that too many things can go out of my control.....I thought I was finished command line with dos 3.3, but it looks like it is here alive and kicking in linux....

---

### Post by coffeecat on 2011-07-26
> **bobk_nyc said:**
>  it looks like it is here alive and kicking in linux....

It is alive and kicking only if you want it to be alive and kicking. Your original issue of installing the Microsoft core fonts you complicated unnecessarily by using apt-get in the terminal. My guess is that you tripped up on signing the EULA in the terminal, which catches a few people out. If you wanted the MS core fonts package installed, why did you not use the Software Centre? And, as I said earlier, if you have a *ttf font file you want installing, you just double-click on it. No terminal involved there.

Oh, and the command line is alive and kicking in Windows 7 still. Have a look around the Microsoft support pages. There are plenty of repair tasks that can only be accomplished from the command line.

---

