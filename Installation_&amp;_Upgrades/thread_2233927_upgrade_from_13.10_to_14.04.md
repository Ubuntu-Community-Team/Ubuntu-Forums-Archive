---
title: "upgrade from 13.10 to 14.04"
date: 2014-07-11
forum: Installation &amp; Upgrades
---

### Post by Yashpreet on 2014-07-11
I was upgrading my laptop from the version 13.10 to 14.04.  During installation, a message popped up saying installation could not proceed as computer is unstable however after restarting the computer, the mouse is frozen in the middle of the screen flashing on and off and a message keeps flashing saying report a problem however I am unable to click anything as the cursor will not move. Please Help!

---

### Post by Bucky Ball on 2014-07-11
Welcome. Was 13.10 running fine prior to attempting to upgrade to 14.04? How did you upgrade? Is this through Software Updater or a terminal or are you talking about a clean install of 14.04 over the 13.10 partition?

[QUOTE=Yashpreet]During installation, a message popped up saying installation could not proceed as computer is unstable [/QUOTE]

This kind of indicates that things were not well prior to the upgrade. If you were upgrading because 13.10 had an issue you couldn't resolve, what was that issue? It might lead us to the reason for this one. :-k

---

### Post by Yashpreet on 2014-07-11
thanks! I was running 12.04 and then step by step upgraded to 13.10 and then to 14.04. I upgraded via Software Updater (a message came up saying upgrade from 13.10 to 14.04)

---

### Post by Bucky Ball on 2014-07-11
Pity. Long-term support releases upgrade directly to the next LTS release. Consequently, you can go from 12.04 LTS to 14.04 LTS directly without needing to upgrade through 13.04 and 13.10. This is a long, laborious and often problematic route, and is possibly the cause of your current issues.

Have you backed up your important data? If so, I would probably suggest a clean install of 14.04. If not, I would suggest you do that back up and then install 14.04.

BTW, 12.04 LTS is fully supported until April 2017. Was there a reason you needed to upgrade to 14.04?

---

### Post by Yashpreet on 2014-07-11
I tried going from 12.04 straight to 14.04 but it wouldn't allow me and said that I must upgrade in stages.  How would I do that? And I upgraded as it wouldn't allow me to install important security updates through the Software Updater

---

### Post by Yashpreet on 2014-07-11
Also I cant click anything as the cursor wont move

---

### Post by sudodus on 2014-07-11
***The official way to do it is to wait until the end of July or beginning of August***, when the first point release will arrive, 14.04.1 LTS. At that time there will be a tested and debugged updater from 12.04 LTS to 14.04 LTS.

-o-

***Not Recommended:***
[I][B]
Only if you have a good backup[/B][/I], you can try to run the script 'early' with the option -d or option -p. I'm not sure in this case what happens, if it might try to upgrade to 14.10. And even if it works reasonably well, you might have to do a lot of fixing and tweaking to succeed.

```
 From man do-release-upgrade
```

```
NAME
       do-release-upgrade - manual page for do-release-upgrade

SYNOPSIS
       do-release-upgrade [options]

DESCRIPTION
       Upgrade  the  operating  system  to the latest release from the command-line.  This is the pre&#8208;
       ferred command if the machine has no graphic environment or if the machine is  to  be  upgraded
       over a remote connection.

OPTIONS
       -h, --help
              show help message and exit

       -d, --devel-release
              Check if upgrading to the latest devel release is possible

       -p, --proposed
              Try upgrading to the latest release using the upgrader from Ubuntu-proposed

       -m MODE, --mode=MODE
              Run  in  a  special  upgrade mode. Currently "desktop" for regular upgrades of a desktop
              system and "server" for server systems are supported.

       -f FRONTEND, --frontend=FRONTEND
              Run the specified frontend

       -s, --sandbox
              Test upgrade with a sandbox aufs overlay

SEE ALSO
       update-manager(8), apt-get(8)
```

---

### Post by sudodus on 2014-07-11
> **Yashpreet said:**
> I tried going from 12.04 straight to 14.04 but it wouldn't allow me and said that I must upgrade in stages.  How would I do that? And I upgraded as it wouldn't allow me to install important security updates through the Software Updater

> **Yashpreet said:**
> Also I cant click anything as the cursor wont move

If you have no good backup, and must save your crippled 13.10 system, I suggest that you run in text mode. Boot with the option **text** (enter it in grub at the other boot options **quiet splash** and reboot. See this link

[https://help.ubuntu.com/community/Grub2/Setup#A.2BAC8-etc.2BAC8-default.2BAC8-grub](https://help.ubuntu.com/community/Grub2/Setup#A.2BAC8-etc.2BAC8-default.2BAC8-grub)

And then you can try with these command lines (originally posted by *oldfred*)

Use [SIZE=3]*sudo -i*[/SIZE]

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

---

