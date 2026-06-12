---
title: "Install 13.4 then software update now no typing after login"
date: 2014-02-28
forum: Installation &amp; Upgrades
---

### Post by bedfordd on 2014-02-28
[Sorry - typo - I have 13.10 (saucy) installed] yes, an odd one. I installed 13.10 (after running 12.4) and when prompted by Software Updater to update I said sure. After reboot I login fine but when I launch Terminal, FireFox, LibreOffice, Thunderbird - I cannot type - no delete key, no backspace no Return/Enter, nothing - except for one exception - the Password field on a brewer page works! 

Also, the Keyboard Layout Chart works fine as does Xterm. After ctl-alt-F1 I can also type at the prompt just fine.

I don't see anything odd in Xorg.0.log or lighted.log. Any ideas?  Thanks, -don

<add> One possible hint, I tried logging in as "Guest" and everything worked. I them moved my .gnome2* .bash* .compiz* fontconfig to a directory and logged out. When I logged in no difference... </add>

<edit>Corrected typo to 13.10</edit>

---

### Post by sudodus on 2014-03-01
The version 13.04 passed end of life in January, and updating/upgrading might not work properly. I think you have better luck with a supported version, either 12.04 LTS or 13.10. So I suggest that you try a fresh installation of either of these (unless you are trying Lubuntu, where the only current version is 13.10).

- 12.04 LTS is more polished, debugged and stable

- 13.10 is newer, has drivers for really new hardware and some newer program versions

---

### Post by bedfordd on 2014-03-01
My bad. I miss-typed. I have 13-10 installed...

---

### Post by sudodus on 2014-03-01
Since it works to use the command line, I suggest that you run a set of commands to make sure your system is updated correctly. Well we know it is not, but this way it may be improved. The tips come from oldfred, one of the most experienced helpers at the Ubuntu Forums.

You can use ***sudo*** in front of each command or do as described: ***sudo -i*** first ... and ***exit*** afterwards (to return to normal privileges)

```
# This will reinstall if not current. (from my chroot procedure which does not have sudo on every line,
# so use the sudo -i first).
 
#if not chroot use: sudo -i

#houseclean
apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean

#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade

# fix Broken packages -f 
sudo apt-get -f install
dpkg --configure -a
```

*Edit*: But since ***guest*** is OK, there might be something wrong with the settings of your user id. Can you remember doing something, that might cause the trouble (something else than updating the program packages)?

---

### Post by bedfordd on 2014-03-01
All reported 0 upgraded, 0 newly installed, 0 to remove & 0 not upgraded...

I'm marking solved as I created another user, moved all my files to a sub-directory, copied from the new user into my home did and then slowly copied my original files back. Everything works but I still don't know what the problem was...

---

