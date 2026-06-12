---
title: "Unattended Ubuntu upgrade is a pain - please fix!"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by gersoid on 2008-05-17
Why is there no option, either in the Update-Manager app or via apt on the command line, to do a truly unattended update 7.10 -> 8.04. i want a 

--keep-config-files 

option. Right now, I know it will chug away, then 30-40 minuutes in, I'll get asked about keeping / replacing the config files for various packages (cups, hplip, apache, samba...happens with about 8 packages in my configuration). And if I'm not around, it will just hang there.

I would like an option on upgrade launch which says "I want to keep using all my existing config files in all packages. Please save new package's config files as xxx.conf.new and I'll sort it out myself later after reading the release notes"

Right now this is a real pain in the backside, and contrasts with the unattended Vista Sp 1 upgrade I did on the same machine - and which went flawlessly.

---

### Post by Malac on 2008-05-28
> **gersoid said:**
> Why is there no option, either in the Update-Manager app or via apt on the command line, to do a truly unattended update 7.10 -> 8.04. i want a 

--keep-config-files 

option. Right now, I know it will chug away, then 30-40 minuutes in, I'll get asked about keeping / replacing the config files for various packages (cups, hplip, apache, samba...happens with about 8 packages in my configuration). And if I'm not around, it will just hang there.

I would like an option on upgrade launch which says "I want to keep using all my existing config files in all packages. Please save new package's config files as xxx.conf.new and I'll sort it out myself later after reading the release notes"

Right now this is a real pain in the backside, and contrasts with the unattended Vista Sp 1 upgrade I did on the same machine - and which went flawlessly.
Heartily agree, this is a pain as you can guarantee that as soon as you leave the machine to do it's stuff a question will popup asking for some confirmation and instead of it upgrading for two hours it sits there at the prompt.

My suggestion would be a flag in packages that are going to be installed/upgraded which need some sort of confirmation/prompt either happening at the end of the process or at the very beginning. I suspect this may throw up dependency issues but that could be taken into account too.

---

### Post by Bubba64 on 2008-05-28
> **gersoid said:**
> Why is there no option, either in the Update-Manager app or via apt on the command line, to do a truly unattended update 7.10 -> 8.04. i want a 

--keep-config-files 

option. Right now, I know it will chug away, then 30-40 minuutes in, I'll get asked about keeping / replacing the config files for various packages (cups, hplip, apache, samba...happens with about 8 packages in my configuration). And if I'm not around, it will just hang there.

I would like an option on upgrade launch which says "I want to keep using all my existing config files in all packages. Please save new package's config files as xxx.conf.new and I'll sort it out myself later after reading the release notes"

Right now this is a real pain in the backside, and contrasts with the unattended Vista Sp 1 upgrade I did on the same machine - and which went flawlessly.

A fresh install after the 1st 10 minutes of checking the CD and passwords and name and partitioning can be ignored, back up what you want to save and install.

---

### Post by gelowe on 2008-08-19
The prompts that appear after a package has been installed/updated/upgraded have to do with dpkg. In the dpkg docs there is reference how to control the dpkg tool. If you run apt-get lines with DEBIAN_FRONTEND=noninteractive pre-pended then no prompts will be given. I am also attaching a document that describes some of the other options. Also you still need to put in the –q –y flags as those are for apt and not dpgk. So for example a dist update would be 

DEBIAN_FRONTEND=noninteractive apt-get -q -y dist-upgrade

[http://www.fifi.org/cgi-bin/man2html/usr/share/man/man8/debconf.8.gz](http://www.fifi.org/cgi-bin/man2html/usr/share/man/man8/debconf.8.gz)

---

