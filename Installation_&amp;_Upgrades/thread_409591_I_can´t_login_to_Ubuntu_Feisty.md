---
title: "I can´t login to Ubuntu Feisty"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by atari130xe on 2007-04-14
Hello forum I have searching all over the net because last night I have been upgrading Ubuntu Feisty Fawn beta version in my box, but after dowload my PC stuck and had to reboot then I couldnt login as usual I get this:

"GDM could not write to your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, it is not possible to log in. Please contact your system administrator"

I got enough space (at least 17GB) so there is no problem with HD space. any help?
thanks in advance! :confused:

---

### Post by zvacet on 2007-04-14
Try to boot in recovery mode and see what hepened.

---

### Post by atari130xe on 2007-04-14
Already done and nothing :( , Im kinda newbie in Linux and I know just a few things. I can´t do nothing if I can´t solve this (My PC is unusable) :(

---

### Post by viper on 2007-04-14
[http://ubuntuforums.org/showthread.php?t=408253&page=27](http://ubuntuforums.org/showthread.php?t=408253&page=27)

Try this tread out, could help you.......

---

### Post by jnuak on 2007-04-22
I'm having the same problem with "GDM not able to write to authorization file"...I've tried rebooting under every mode I know how to (I don't know much...), but with no luck.  I tried adduser to see if building a new user would let me log in, and I still get the same error.  I also looked at the link to the thread posted above, and if there is something helpful there, I certainly don't know how to do anything with--a dumbed down explanation of how that helps is needed if I'm going to get it.  If someone has an idea, please say so soon because I've got a paper due tomorrow...

---

### Post by rainwalker on 2007-04-22
I'm not sure if this will help, but I just had an experience earlier today where I couldn't get past logging in because I was out of disc space. What I did was
1. Type CTRL+ALT+F1 on the login screen (sends you to text-based login)
2. Login to your account
3. Type 'df -h' to see what the '/' partition has as far as available space
4. Remove (rm [filename]) unnecessary files to free up space
5. Reboot
6. Login normally

And it worked for me. Again, though, I'm not sure if this is what you're talking about.

---

### Post by jnuak on 2007-04-22
I've tried deleting files, and I've gotten rid of about 10-15G of files I luckily have on an external HD, but I still can't get it to let me log in.  It seems to have even gotten worse now.  Now I can't even get to a login screen before it starts giving me this "mmcblk0 error1 somethingsomethingsomething."  Really turning into a headache here...I managed to get to a command prompt when I rebooted in recovery mode under an older kernel, but now I can't even get that.  I'm going to try to get some more useful information about what my computer is doing when it gets through its forced check of sda1.

---

