---
title: "Forced to reset compiz/unity after each linux-headers upgrade"
date: 2013-06-04
forum: Installation &amp; Upgrades
---

### Post by waallen on 2013-06-04
Good morning everyone, I've been using Ubuntu (currently 13.04) for a bunch of months now and I was wondering if it's acceptable to have to reset compiz and unity (with ```
dfconf reset -f /org/compiz
``` and ```
setsid unity
``` after every linux-headers/linux-generic upgrade. 
Right after that on the first boot, I am prompted with the desktop having no bars. I tried looking for other cleaner methods such as just re-installing the ATI proprietary drivers, cleaning the compiz-1 folder but none of them worked. Is there any other way to prevent this behavior besides resetting both compiz and unity configurations?

---

### Post by waallen on 2013-06-05
Bump

---

### Post by bogan on 2013-06-06
Hi!, **Waallen,**

I had the same  blank Desktop problem after updating 13.04 on three different installations.

Neither the dconf reset, nor various Compiz reset commands, worked for me as I had 'unable to open display' & 'GLX Plugin not loaded' errors.

What did work for me is the code below using the '--reset-unity' option included in 'Unity-tweak-tool', run from a new Admin account, or when logged in to Gnome fallback.

Note: you may need to use 'sudo' instead of 'gksudo', or neither, as there is a Post that gksudo gave an 'unrecognised command' message.

[COLOR=#0000ff]I did not have to run the reset again after later more recent kernal updates[/COLOR].

**Originally Posted by bogan in Ubuntu +1**: [http://ubuntuforums.org/showthread.php?t=2136435](http://ubuntuforums.org/showthread.php?t=2136435) There is a long list of alternative reset commands in that Thread. [ Posts #39 & #36']
Quote:
 My Blank Desktop problem with 13.04 has been cured by using a  terminal in Fallback  mode to enter the reset-unity command included in  Unity-Tweak-Tool: ```
sudo apt-get install unity-tweak-tool 
echo $DESKTOP_SESSION 
  fallback-compiz    
gksudo unity-tweak-tool --reset-unity  
Warning: You are about to reset unity to its default configuration. 
   It is normal for your desktop to flicker during the process.    
Type yes to continue, anything else to exit.      Do You wish to continue? _ 
```_**On rebooting**_, all the log-in options' displays were correct and with intact Launchers and Panels.

 Running the same commands when logged into the faulty Ubuntu/Unity  Blank  Desktop gave a 'Can not open display' message and did nothing.

It is probable - though I have not tried it - that the other compiz/unity reset commands would also work if run in the same way.                      

Chao!, **bogan.**

---

