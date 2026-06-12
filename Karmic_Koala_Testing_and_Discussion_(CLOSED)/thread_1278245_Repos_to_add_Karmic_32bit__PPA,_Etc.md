---
title: "Repos to add Karmic 32bit?  PPA, Etc?"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by virtualu2 on 2009-09-29
Hi,
I had alot of issues with Jaunty and have found Karmic is working much better on my laptop so far.

Can someone let me know which repos to add?  I like to use Thunderbird, Firefox, Opera, Seesmic or tweetdeck, adobe flash, acrobat reader, etc.

Opera has always been the biggest issue for me on distros I have used, it is SLOW over wireless....Does anyone know why?  

I also want to use compiz as well.

Thanks and if you can let me know the best way to add them, that would be great!

This is the best version of Ubuntu yet!

---

### Post by dino99 on 2009-09-29
remind that it's still alpha
so, ppa are not numerous: kernel mainline, video driver
but very risky, better to stay on the basic repo at time

---

### Post by Colonel Kilkenny on 2009-09-29
> **virtualu2 said:**
> 
Opera has always been the biggest issue for me on distros I have used, it is SLOW over wireless....Does anyone know why?

Sounds like it might be a ipv6 & DNS problem. You can try to disable ipv6 from your system and see if it helps. I'm not sure what is the best way to do it with Karmic though.

---

### Post by drs305 on 2009-09-29
An easy way to manage repositories is via Syanaptic (System, Administration, Synaptic Package Manager).

Once you have it open, go to Settings, Repositories, and look at the tabs:

Ubuntu Software: Normally users have the first 4 enabled - main, universe, multiverse, restricted. (Firefox 3.5, Thunderbird 2.0, Compiz)

Other Software: Enable Canonical Partner  (Acrobat if you have 32 bit)

Updates: Enable at least the Security updates, and normally the Recommended updates.

To add the popular Medibuntu repository and import the public key, run this command:
```

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update

```

Compiz is installed by default. 

To learn more about Repositories, visit the Ubuntu wiki:
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by slakkie on 2009-09-29
For medibuntu I use the following script:

```

#!/usr/bin/env bash

# Check if we are on Ubuntu
if [ "$(lsb_release -is)" != "Ubuntu" ] ; then
    echo "This script is only intended to run on Ubuntu"
    exit 255
fi

# Check if we are root
if [ $UID -ne 0 ] ; then
    echo "Please run this as root!"
    exit 255
fi

# Get distro
distro=$(lsb_release -cs)

# Check if medibuntu repo is already present
cat /etc/apt/sources.list | grep -v "^#" | grep "packages.medibuntu.org" &>/dev/null
if [ $? -ne 0 ] ; then
    # Add them if not and update
    echo "deb http://packages.medibuntu.org/ $distro free non-free" >> /etc/apt/sources.list
    wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | apt-key add -
    aptitude update
fi

# Finally, install all the packages
aptitude install gstreamer0.10-ffmpeg ubuntu-restricted-extras vlc mplayer mozilla-plugin-vlc mozilla-mplayer libdvdcss2 non-free-codecs

```

---

### Post by DougieFresh4U on 2009-09-29
There is also the 'Mozilla' repo as well.

---

### Post by virtualu2 on 2009-09-29
Thanks everyone!  I will keep it to the defaults, but is it safe to add Mozilla and Adobe right now?

---

### Post by virtualu2 on 2009-09-29
Thanks for the info, I think I am good with the repos, but Opera is still slow...

I heard before that it could be IPV6, how do I disable that in Karmic?

---

### Post by DougieFresh4U on 2009-09-29
> **virtualu2 said:**
> Thanks everyone!  I will keep it to the defaults, but is it safe to add Mozilla and Adobe right now?

I am using the Mozilla repo with no problems.
It will give you Thunderbird 3.0 which works great for me and I also am trying out Firebird 3.6 & 3.7 beta's

---

