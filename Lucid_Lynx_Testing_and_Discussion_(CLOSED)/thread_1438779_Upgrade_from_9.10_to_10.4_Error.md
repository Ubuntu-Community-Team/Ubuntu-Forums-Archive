---
title: "Upgrade from 9.10 to 10.4 Error"
date: 2010-03-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by villindesign on 2010-03-25
I used the updated to 10.4 from 9.10 using the command ```
update-manager -d -c
```

My computer froze after the packages had been downloaded, and during the installation of those packages. I rebooted, but grub did not load. I tried ```
sudo apt-get dist-upgrade -f
```, but I get an error "could not perform immediate configuration on already unpacked 'udev'". How can I get my OS upgraded to 10.4? Thank you

---

### Post by Mark Phelps on 2010-03-25
Lucid is still in development and, as such, Lucid-related questions should be posted to Development & Programming, Lucid Lynx Testing.

Will be requesting the Mods move this thread accordingly.

Please look for responses there.

---

### Post by lidex on 2010-03-26
> **villindesign said:**
> I used the updated to 10.4 from 9.10 using the command ```
update-manager -d -c
```

My computer froze after the packages had been downloaded, and during the installation of those packages. I rebooted, but grub did not load. I tried ```
sudo apt-get dist-upgrade -f
```, but I get an error "could not perform immediate configuration on already unpacked 'udev'". How can I get my OS upgraded to 10.4? Thank you

Not really a good idea to upgrade a stable install to a beta. If you want to test lucid, download the beta iso and install to a separate partition. you can use that or the LiveCD to salvage your data from the botched upgrade.
[http://www.ubuntu.com/testing]("http://www.ubuntu.com/testing")

---

### Post by nanog on 2010-03-26
See my sig.

Specifically dpkg --configure -a and apt-get install -f.

Should fix most problems...

---

### Post by nanog on 2010-03-26
> Not really a good idea to upgrade a stable install to a beta. 

But it sure is fun!

---

### Post by tilixibr on 2010-03-26
What I'll do is upgrade to beta on a external HD with 9.10, so I don't screw up the HD that I actually use :)

---

### Post by lidex on 2010-03-26
> **tilixibr said:**
> What I'll do is upgrade to beta on a external HD with 9.10, so I don't screw up the HD that I actually use :)
I think upgrade is cool for stable releases but you'd be better off with a fresh beta install.

---

### Post by tilixibr on 2010-03-26
I tried upgrading by mounting my disc image but it didnt work.... :(And I'm running low on CDs, so I dont' want to burn one.... check this thread i just posted [http://ubuntuforums.org/showthread.php?t=1439977&highlight=upgrade](http://ubuntuforums.org/showthread.php?t=1439977&highlight=upgrade), I'm desperate :(

---

### Post by QLee on 2010-03-27
I'm a little confused tilixibr, you seem to have jumped into villindesign's thread. This might not help with what might have happened to your upgrade but I will say that I have successfully completed an upgrade from 9.10 to Lucid. It's not exactly the same as the method you used because I upgraded at alpha stage and I used a 'Net connection. I'm now at beta due to upgrades since then. Did you make sure your 9.10 install was fully upgraded and working well previous to trying the upgrade to Lucid?

---

### Post by tilixibr on 2010-03-27
Yes, I had all my updates installed yesterday, including the new kernel image and all updates for minor programs (such as aislesolitaire), My update list was empty, all it had was the new version message

---

### Post by QLee on 2010-03-27
Just to be clear, you are using the "alternate CD" image as per the instructions.

This very recently fixed bug seems to be related to the problem you had.
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/527870](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/527870)

If one is going to test pre-release, it's a good idea to become accustomed to forum searches and the information returned by search engines.

---

