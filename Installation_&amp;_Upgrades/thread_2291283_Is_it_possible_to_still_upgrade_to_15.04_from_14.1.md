---
title: "Is it possible to still upgrade to 15.04 from 14.10"
date: 2015-08-19
forum: Installation &amp; Upgrades
---

### Post by alison3 on 2015-08-19
I got the message to upgrade a few weeks ago, but for some reason thought I'd have more time.  So when I tried to upgrade today ofc I got the message that 14.10 is not supported anymore.  I tried to do this:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
(i put this in the list.sources file:

## EOL upgrade sources.list
# Required
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) utopic main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) utopic-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) utopic-security main restricted universe multiverse


# Optional
#deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) utopic-backports main restricted universe multiverse)

But it doesn't seem utopic is available for this.  It says file not found and what not.  It would just be nice if I could upgrade instead of doing a clean install and having to wait hours upon hours of putting all my backup stuff back in linux.  Next time I'll just upgrade when it tells me to, but first of all is it even possible?


also I know if I do a re-install, I can keep my home folder, but can I do this for an install of a different version?

---

### Post by Irihapeti on 2015-08-19
The main thing that's likely to go wrong (if it does) with keeping your home folder, is the configurations in the hidden folders not working with later versions of the programs.

If that does happen, the remedy is to remove the hidden folder in question and let the program create a new set of config files.

I would still recommend that you have a backup anyway, just in case something goes wrong.

---

### Post by alison3 on 2015-08-19
I do have backups, but what I'm asking is if i can still upgrade or if I have to do a clean install of the newer version?

---

### Post by Irihapeti on 2015-08-19
14.10 doesn't appear to be listed in old-releases.ubuntu.com  In that case, you can't do an upgrade - unless someone else has another idea, that is.

If no one comes up with another option, then a clean install would be your only choice.

---

### Post by plucky on 2015-08-19
Utopic Unicorn (14.10) support ran out on July 23 

So the repos should be closed.

What happens if you run ```
sudo apt-get update
```?

---

### Post by grahammechanical on 2015-08-19
It is my understanding that we can use the old-releases archives if the release we are using has reached end of life and the next release has also reached end of life but we do not need to use the old-releases method if the next release is still in its support period. So, it should be possible to upgrade from Ubuntu 14.10 to Ubuntu 15.04 even though 14.10 is at end of life because 15.04 is still in its support period. At least until the end of January 2016.

The Update Manager should also be giving you an option to start the upgrade. You may have complicated the problem by changing the sources list URLs to point to the old-releases archives. Try going to Software & Updates and re-setting the main server to the usual Utopic servers. Then update and see if Update Manager gives the warning about 14.10 being end of life. It should also give you a button to click to start the upgrade.

Regards.

---

### Post by alison3 on 2015-08-19
> **grahammechanical said:**
> It is my understanding that we can use the old-releases archives if the release we are using has reached end of life and the next release has also reached end of life but we do not need to use the old-releases method if the next release is still in its support period. So, it should be possible to upgrade from Ubuntu 14.10 to Ubuntu 15.04 even though 14.10 is at end of life because 15.04 is still in its support period. At least until the end of January 2016.

The Update Manager should also be giving you an option to start the upgrade. You may have complicated the problem by changing the sources list URLs to point to the old-releases archives. Try going to Software & Updates and re-setting the main server to the usual Utopic servers. Then update and see if Update Manager gives the warning about 14.10 being end of life. It should also give you a button to click to start the upgrade.

Regards.
Okay seems to be working, but time will tell I guess...


I think the problem was somewhere buried in all my Software URLs was an old one for Trusty.  Not even sure why that was in there.  I think that was causing the problem.  Thank you, I'll let you know if there's any other problems.

---

