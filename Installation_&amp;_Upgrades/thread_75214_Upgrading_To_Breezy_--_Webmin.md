---
title: "Upgrading To Breezy -- Webmin"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by Freddie on 2005-10-13
I am in the process of upgrading my 5.04 system to 5.10. First I did an apt-get update and then an apt-get upgrade. However, one of the packages which is tried to upgrade was webmin. However, because the version of webmin in the repositories is always weeks out of date I had taken to using the auto-update feature of webmin which worked fine until the stupid version of apt went mental trying to upgrade it. I am now left with no webmin and unable to use apt because it keeps complaining about packages (it amazes me how if a file can not be removed because it can not be found how the package can not be removed, as if it can not be found then it is not there and so there is no need to deleted it). Can anyone help me get to Breezy and then I will reinstall webmin, however first I need to tell apt that it really is gone.
I had a perfectly working system until apt, thinking that it knew everything tried to upgrade a package.

---

### Post by Freddie on 2005-10-13
Currently I just need a way for apt to forget about a few packages and then everything will be back to normal (I will install webmin as manually next time to stop this from happening).

---

### Post by Freddie on 2005-10-15
Does anyone have any ideas? Until Apt stops trying to configure packages which don't exist I am not only unable to upgrade to breezy but also unable to upgrade anything.

---

### Post by WiFi Net Guy on 2005-10-26
I'm having the same problem right now trying to upgrade. Any ideas?

---

### Post by Irony on 2005-10-26
Is it not simpler to use Synaptic? I seem to recall apt-get being a bit funny with 'lost' packages.

I upgraded by downloading the Breezy .iso and upgrading via synaptic and the cd rom.

---

### Post by WiFi Net Guy on 2005-10-26
Freddie, I know this is probably too late, but I just got it working myself and hopefully this will help anyone else that runs into this problem. 

To fix it for me, I had to go find another webmin.acl and update.conf and then copy those to the /etc/webmin directory. After that, I was able to first apt-get install webmin and have it complete correctly, including being able to configure my webmin-core, etc. After that, apt-get worked without yelling.

Hope this helps...
Alvin

---

### Post by AzureCerulean on 2005-10-28
[COLOR="DeepSkyBlue"]no, synaptic will not solve this issue nor will coping the files over atleast as far as i have found.  have attempted forcing webmin to (re)install.  but because other modules also so incorrect version in  dpkg/apt/synaptic  you can neither (re)install/remove packages.[/COLOR]

---

### Post by Remmelas on 2005-10-28
[QUOTE=AzureCerulean][COLOR="DeepSkyBlue"]no, synaptic will not solve this issue nor will coping the files over atleast as far as i have found.  have attempted forcing webmin to (re)install.  but because other modules also so incorrect version in  dpkg/apt/synaptic  you can neither (re)install/remove packages.[/COLOR][/QUOTE]
I'm sure there's a better way, but the last time i got myself into a loop where i couldn't remove or upgrade a package, i'd just see what file apt-get was looking for, then touch /what/ever/the/file/path/is

lather, rinse, repeat

---

### Post by Freddie on 2005-11-02
Yes, I made a post on the Debian mailing list and the best way to do it is to find out what files are missing and then touch them. With the errors about pre-removal scripts I just commented out '#' everything in the 'if' block and it worked.

---

