---
title: "Unity-greeter segfault after upgrade to 11.10"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by straxus on 2011-10-14
From syslog:

```
[   42.542925] init: plymouth-stop pre-start process (2204) terminated with status 1
[   44.526208] unity-greeter[2186]: segfault at 0 ip 00c7ecbb sp bfe7a280 error 4 in libgio-2.0.so.0.3000.0[be6000+142000]
[   45.704354] unity-greeter[2240]: segfault at 0 ip 00829cbb sp bfdb7980 error 4 in libgio-2.0.so.0.3000.0[791000+142000]
[   46.947393] unity-greeter[2282]: segfault at 0 ip 00700cbb sp bffea150 error 4 in libgio-2.0.so.0.3000.0[668000+142000]
[   48.046982] unity-greeter[2372]: segfault at 0 ip 00d05cbb sp bfdc3e80 error 4 in libgio-2.0.so.0.3000.0[c6d000+142000]
[   49.393550] unity-greeter[2511]: segfault at 0 ip 00e88cbb sp bfdba350 error 4 in libgio-2.0.so.0.3000.0[df0000+142000]
[   50.406684] unity-greeter[2540]: segfault at 0 ip 0072ccbb sp bfcb5380 error 4 in libgio-2.0.so.0.3000.0[694000+142000]

```

It goes on like that for 50 lines or so.  Any ideas?

---

### Post by straxus on 2011-10-14
Fixed.  I purged unity-greeter & gdm, and then edited /etc/lightdm/lightdm.conf and removed this line:

greeter-session=unity-greeter

---

### Post by 23dornot23d on 2011-10-14
Nice one - mark as solved and I will add it in my listincase anyone else needs
a similar solution .... ty

---

### Post by jaydeuce on 2011-10-17
Thanks for posting this. I had the same problem on two machines - I've read lightdm + unity-greeter + NVIDIA proprietary drivers don't play nicely together on the latest versions. Commenting out the unity-greeter line in my lightdm.conf file did the trick. Tried switching to gdm but the display appeared all screwy, so stick with lightdm.

Now on to figure out how to make Mythbuntu auto-login and make my Packard Bell remotes work in LIRC again :)

---

### Post by straxus on 2011-10-17
Awesome.  It's good to know that helped someone else. :)

Auto login is also setup in /etc/lightdm/lightdm.conf now.  Here's what mine looks like:

```
[SeatDefaults]
user-session=mythbuntu
allow-guest=false
autologin-user=straximus
autologin-user-timeout=0
autologin-session=lightdm-autologin

```

I also had problems getting my Streamzap remote to work again.  In my case, the button names for my remote had all changed in lirc.  UP became KEY_UP, and OK became KEY_OK, and so on.  You can check this by running irw, and pressing the buttons on your remote.  Your problem may well be different, but it's something to check.

---

### Post by akwala on 2011-10-18
I started seeing the repeating *"unity-greeter ... segfault ... error 4 in libgio-2.0.so.0.3000.0"* upon rebooting after upgrading packages following the Natty->Oneiric upgrade. The display alternates endlessly between the nVidia splash and the boot console; Alt+Ctrl+F1 doesn't drop me into the text console. Booting in recovery mode and dropping into root console allows only read access, so I can't purge unity-greeter or edit lightdm.conf as suggested.

Any suggestions?

---

### Post by straxus on 2011-10-18
See if this will remount your drive as read-write:

```
mount -rw -o remount /
```

---

### Post by akwala on 2011-10-18
> **straxus said:**
> See if this will remount your drive as read-write:

```
mount -rw -o remount /
```

Thanks! That worked, I edited lightdm.conf and purged unity-greeter & gdm.

However, lightdm fails to launch. Syslog shows: [I]"init: lightdm main process ... terminated with status 1."
[/I]

---

### Post by straxus on 2011-10-18
I can suggest a couple of things, but I haven't experienced this particular problem, so I fear I'll be of limited help from this point on.  If this doesn't work, you might want to start a new thread about the error you now have.

See if the package *lightdm-gtk-greeter* is installed.  If not, install it.

You can also try reinstalling lightdm with ```
apt-get install --reinstall lightdm
``` to see if that helps.  Unlikely I think, but something to try.

---

### Post by Waleb on 2011-10-21
> **straxus said:**
> Fixed.  I purged unity-greeter & gdm, and then edited /etc/lightdm/lightdm.conf and removed this line:

greeter-session=unity-greeter

Thank you. This solved my Problem. Took me an hour to get here.

---

### Post by jms-ubuntu-en on 2011-10-28
:mad:
This must be worst Ubuntu release ever, I had all issues in this topic + a couple more in my htpc. Can't wait to upgrade the mythtv backend and two other natty machines :-\"

Thank you for sharing the information!

---

### Post by timbonz on 2011-11-13
Thanks straxus, fixed it for me too, waited till now to update thinking things like this wouldn't happen and upset the WAF...

Regards
Tim

---

### Post by Christophe Agathon on 2011-12-28
Thanks Straxus, it did the trick for me too
Rgds,
Chris

---

### Post by alavers on 2012-01-03
Thanks Straxus - one more solved on Mythbuntu install with Nvidia drviers after 11.04 to 11.10 upgrade.

---

