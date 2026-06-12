---
title: "Problems when upgrading from Dapper lts to Hardy Lts"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by lpc on 2008-05-06
Hello,

I tried to update from Dapper LTS to Hardy LTS and ran into troubles.

What I did was to run:
sudo aptitude update && sudo aptitude upgrade && sudo aptitude dist-upgrade && sudo aptitude autoclean
sudo aptitude install ubuntu-desktop

Then I open /etc/apt/sources.list and replace all dapper instances with hardy.

After that I run 
sudo aptitude update && sudo aptitude upgrade && sudo aptitude dist-upgrade && sudo aptitude autoclean

and restart my laptop (ACER Aspire 3002wlci). 

Then I got an error message saying that xserver failed to start.
I read in a post that I could fix that running:
sudo dpkg-reconfigure xserver-xorg
but got an error message saying that xserver-xorg is broken or not fully installed

So, I tried:
sudo aptitude reinstall xserver-xorg

but got the message "dpkg was interrupted, you must manually run dpkg --configure -a to correct the problem"

Did that, but got a huge list of errors saying "dependency problems prevent configuration of" Among the programs listed are xkeyboard-config, gnome-panel, xserver-xorg, gs-common, ghostscript-x, scribus.

After that nothing works. Any aptitude or apt-get command returns that I should run dpkg --configure -a and dpkg --configure -a keeps returning the long list of errors.

Please, any ideas how I can solve this (note I am in command line mode or in other words can't execute synaptic)?

Thanks!

---

### Post by fixitdude on 2008-05-06
I'm just wondering why you had to "open /etc/apt/sources.list and replace all dapper instances with hardy"? I think the dist-upgrade should have done that.

Possible you ran out of disk space? Do a "df" and see.

Worse case, upgrade from CD.

By the way, you can try "sudo su -" and then be in root all the time, saves a little typing.

---

### Post by lpc on 2008-05-06
It doesn't seem to be a space problem. Disk space reported by df -h is:
4.8G in /dev/hda1
601M /var/run
601M /var/lock
601M /dev
601M /dev/shm
583M /lib/modules/2.6.15-51-386/volatile

I had always modified /etc/apt/sources.list by hand. Didn't know it should have been changed by dist-upgrade.

---

### Post by prshah on 2008-05-06
> **lpc said:**
> 
but got the message "dpkg was interrupted, you must manually run dpkg --configure -a to correct the problem"

Did that, but got a huge list of errors saying "dependency problems prevent configuration of" Among the programs listed are xkeyboard-config, gnome-panel, xserver-xorg, gs-common, ghostscript-x, scribus.



I had the same problem due to a failed upgrade (power went off), and I use the --force-all switch to overcome the dependency problems.

```

dpkg --configure -a --force-all
```


Note that force-all may not be ideal for you; ```
dpkg --force-help
``` will give a list of force options, you should select the most reasonable. I was too lazy to select, and the net result was that while everything worked fine after, all customized config files (samba.conf, blacklist, etc) were replaced with defaults.

---

### Post by fixitdude on 2008-05-06
> **lpc said:**
> It doesn't seem to be a space problem.I may be talking about the old days but you had two partitions, one was / which was like 5G and could fill up easily, it contained all the system type of files, the other was /home.

What I was thinking is that / might have been full. If you had old style stuff from a previous install.

And I am still suggesting a fresh install via CD, there should be a way to do that without wiping out any data from /home, but back up important stuff anyway, the live CD will let you copy files, mount USB drives etc...

I think you pick "manually edit partition table" and just leave things alone and then it will just use what is there, I am not sure and the instructions on the link below isn't clear (bad, bad, bad whoever made those screens, should be more clear when you might wipe out data).

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

I didn't upgrade that way so I don't know, maybe someone else does.

---

