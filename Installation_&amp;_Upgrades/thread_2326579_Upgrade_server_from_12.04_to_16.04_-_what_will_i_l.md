---
title: "Upgrade server from 12.04 to 16.04 - what will i lose?"
date: 2016-06-02
forum: Installation &amp; Upgrades
---

### Post by Rick P. on 2016-06-02
I have a home server set up and running 12.04 very nicely but am getting tired of the "Not all updates can be installed" warnings from old packages that are no longer maintained. I could clean them up but figure I'm due for an upgrade anyway...

The system started out running 8.04 or maybe 9.04 and was upgraded along the way to 12.04 Desktop (not Server) before I actually needed server functions. I added them along the way as i needed them and at this point i don't even remember what they all are. FTP, upsd / upsmon, NTP, smtp, nntp, mdadm (if it's not part of the desktop install), plus Plex, SickBeard and print server services are a few that I can think of. My question is twofold:

1. Is there a tool that shows what packages have been added over time (vs updates to base packages), especially the services I've added on top of 12.04 Desktop? Ideally 
dpkg --get-selections > somefile.txt followed by 
sudo dpkg --set-selections < somefile.txt && sudo apt-get -u dselect-upgrade 

would be sufficient to get be back up and running after I install 16.04 but i don't know if this also works for services / daemons.

2. Assuming it doesn't what besides these should I be looking at backing up? 
/home
/root
/etc
/var
/opt
/media
/mnt

If there are files in some of these folders that might hose a 16.04 install if overwritten do you know what they are? This server is the base for our home TV and I'll be drawn and quartered if I take too much time sorting out an upgrade so thoughts / comments would be appreciated.

---

### Post by ubfan1 on 2016-06-02
This is known as a "production" system, with minimal downtime allowed! ;^)   Things like this always take longer than anticipated, so I'd suggest cloning the system, upgrade on your own schedule, and then swap back a running, checked out, system.  Answer to question 1 might be apt-mark with a show-manual parameter, but I've never been able to easily see that the output is really what I expect.  You might think about adding another root partition on the new system, so future upgrades can be done on an alternate root.  On a system upgraded so many times, you probably would be better off with a fresh install, then add your data/programs.

---

### Post by grahammechanical on 2016-06-02
Anything under /root except /home belongs to the system. Everything in those directories will be replaced. That is the point of upgrading. The upgrade process will calculate what needs to be upgraded/replaced and will do what is necessary.

When you back up those directories do you intend to copy the contents back into the 16.04 directories? Putting old libraries back into those directories and overwriting the newer libraries must surely break the OS.

Put in a fresh dual boot with 16.04. Keep the old system running while you configure 16.04 to meet your needs.

Regards

---

### Post by Rick P. on 2016-06-04
> **ubfan1 said:**
> On a system upgraded so many times, you probably  would be better off with a fresh install, then add your  data/programs.

I was thinking the same thing (vs an  upgrade to 14.04 then 16.04). The 24 TB of data is on RAID arrays so  adding that back is trivial, it's the programs that I've lost track of  along the way and was hoping i could somehow get a complete list of what's been added over time. I can get a full list of what's loaded of course but really only need to know what was added incrementally outside of the base install. Will have to spend some time with the dpkg manual...

---

### Post by ubfan1 on 2016-06-04
Well, get the current list, save it, do the fresh install, get its list,  sort the two lists, and get the uniq report on non duplicated items.  That'll be too much, as some package might have dropped dependenies, but another easy check to make.  apt-mark  with the "showmanual" param might also give you interesting packages, but I could never easily see that the "manual" was really what I installed.

---

### Post by SeijiSensei on 2016-06-04
You can create a list of installed packages with "dpkg --get-selections" then use "dpkg --set-selections" to tell the new system what to install. See "[man dpkg]("http://manpages.ubuntu.com/manpages/precise/man1/dpkg.1.html")" for more details.

---

### Post by Rick P. on 2016-08-02
> **SeijiSensei said:**
> You can create a list of installed packages with "dpkg --get-selections" then use "dpkg --set-selections" to tell the new system what to install. See "[man dpkg]("http://manpages.ubuntu.com/manpages/precise/man1/dpkg.1.html")" for more details.

This is very helpful, thanks!

---

### Post by yoshii on 2016-08-02
If it hasn't already been noted, a lot of others elsewhere on this site are saying to NOT do an online upgrade, and instead do a fresh install and gradually migrate your settings and files over to the new install.  Apparently it's risky these days to do an online upgrade since things can go wrong.  

But yeah, SeijiSensei's advice is very helpful ( "You can create a list of installed packages with "dpkg --get-selections" then use "dpkg --set-selections" to tell the new system what to install. See "[man dpkg]("http://manpages.ubuntu.com/manpages/precise/man1/dpkg.1.html")" for more details." )

Thanks SeijiSensei, I wanted to know how to do that too!

---

