---
title: "Requesting permission before making install permenent"
date: 2012-03-23
forum: Installation &amp; Upgrades
---

### Post by helmcken on 2012-03-23
[FONT="Century Gothic"][SIZE="1"][COLOR="Black"]When I select INSTALL UBUNTU, Ubuntu presents me with the " enter your administrators password" box. As I have never set a password, I have no idea what to enter! Leaving it blank and pressing enter does not work! All wrong answers receive either** Incorrect password, try again** or the _error message_: **  Failed to run    /usr/ bin/ubiquity'gtk_ui' as user root.** Therefore, I cannot get the machine to make the install permanent!!
    I downloaded Ubuntu ver.10.04-LTS-desk-amd64 and the wubi and ran the md5 hash check which showed a good, clean copy. So I burned it to disc and verified disc. Then I inserted disc into machine that I want to install on and selected check disc from Ubuntu list. The tool reported the disc to be okay. This machine has Win 7-64bit running correctly on it. 
    After selecting language, it does NOT matter whether I choose "Try first.." or "Install" as machine ALWAYS builds the "Try first without any changes" desktop. When this Ubuntu desktop is ready, I AM UNABLE TO ACCESS TERMINAL! Terminal/ command prompt starts in bottom bar, but disappears after 2 seconds.
    *** How do I solve this? How do I make my Ubuntu install permanently?*** [/COLOR][/SIZE][/FONT]

---

### Post by PhantomTurtle on 2012-03-23
If there is a way you can open terminal then you can add a sudo password in the live cd,
```
sudo passwd ubuntu
```
IF you cannot open terminal, switch to tty1 and change the sudo password with Ctrl + Alt + F1 and then try again

---

### Post by critin on 2012-03-23
> **helmcken said:**
> [FONT=Century Gothic][SIZE=1][COLOR=Black]When I select INSTALL UBUNTU, Ubuntu presents me with the " enter your administrators password" box. As I have never set a password, I have no idea what to enter! Leaving it blank and pressing enter does not work! All wrong answers receive either** Incorrect password, try again** or the _error message_: **  Failed to run    /usr/ bin/ubiquity'gtk_ui' as user root.** Therefore, I cannot get the machine to make the install permanent!!
    I downloaded Ubuntu ver.10.04-LTS-desk-amd64 and the wubi and ran the md5 hash check which showed a good, clean copy. So I burned it to disc and verified disc. Then I inserted disc into machine that I want to install on and selected check disc from Ubuntu list. The tool reported the disc to be okay. This machine has Win 7-64bit running correctly on it. 
    After selecting language, it does NOT matter whether I choose "Try first.." or "Install" as machine ALWAYS builds the "Try first without any changes" desktop. When this Ubuntu desktop is ready, I AM UNABLE TO ACCESS TERMINAL! Terminal/ command prompt starts in bottom bar, but disappears after 2 seconds.
    *** How do I solve this? How do I make my Ubuntu install permanently?*** [/COLOR][/SIZE][/FONT]

If you have installed Wubi, ubuntu is already permanent.  It is running similar to a Windows program except you open it via the start-up screen instead of choosing a program.

There is no 'Try First' with Wubi.  Is this a brand new install?  Have you restarted and do both Windows and Wubi (Ubuntu) show on the start up screen?  

Not quite sure what the issue is.

---

### Post by PhantomTurtle on 2012-03-23
> **critin said:**
> If you have installed Wubi, ubuntu is already permanent.  It is running similar to a Windows program except you open it via the start-up screen instead of choosing a program.

There is no 'Try First' with Wubi.  Is this a brand new install?  Have you restarted and do both Windows and Wubi (Ubuntu) show on the start up screen?  

Not quite sure what the issue is.

I think he means that he is trying to install it from a live cd/usb and the installer wont launch.

---

### Post by helmcken on 2012-03-23
To Critin: This is a new install attempt from a disc. Yes, it is running Ubuntu similar to a Windoze program. I want to select "Install" to make Ubuntu install permanent in a dual-boot with the existing Win 7. But, in that temporary mode, cannot install. Must power off or reboot. When I do either, Win 7 boots as normal with no sign of Ubuntu anywhere. 
    I have NEVER set a password and canNOT access terminal to go sudo with commands. What to do?

---

### Post by helmcken on 2012-03-23
> **PhantomTurtle said:**
> 
IF you cannot open terminal, switch to tty1 and change the sudo password with Ctrl + Alt + F1 and then try again

[FONT="Century Gothic"][SIZE="1"][COLOR="Black"]Phantom Turtle: How do I do that? Meaning when and where do I switch this TTY. Also, in order to change sudo password, I must enter original password. I NEVER CREATED A PASSWORD. How do I guess what that is?[/COLOR][/SIZE][/FONT]

---

### Post by helmcken on 2012-03-24
I solved this myself. I downloaded, md5-hash-checked, burned to disc and verified burn on the non-64bit-version! **When I ran the Ubuntu 10.04.4-desk-i386.iso version, it actually installed as it is supposed to!** Now, I do not know why the 64-bit version of Ubuntu will not install on a 64-bit architecture computer currently running Win 7-64bit. All I can say *is if you are experiencing these same troubles, try this fix! *
Thank-you to all who replied in attempt to help!

---

