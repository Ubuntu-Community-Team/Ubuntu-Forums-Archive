---
title: "[SOLVED] Unable to login after 8.10 upgrade"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by blueyelabs on 2008-10-31
I just upgraded to Intrepid and several problems arose.

When I first booted the computer (the cleaner switched it off at the plug before I could get downstairs, although I left the upgrade going all night so it should have completed) the boot process hung saying something about read only files/directories.
I then went into recovery mode and tried to fix broken packages &c. which didn't work because in the recovery mode there is no network for some reason...
Anyway, I tried booting again (thinking it had worked, because I didn't read properly) and it went to the gdm login screen but I couldn't type, or use the mouse except to CTRL-ALT-DEL a reboot. I know that the keyboard was working and the mouse, because the wireless receiver responded, and I could type in the root shell part of recovery mode.
I assumed this to be an xserver issue, so I ran xfix from recovery mode. This broke the xserver and so I restored my previous configuration (which xfix kindly backed up). So now I'm at the point where I can't login normally, and have an "unreachable" network in the root shell and the whole of recovery mode so I can't update aptitude or fix everything with dpkg.
I desperately need to get this working BEFORE my parents get home because they will probably kill me. I can't just fresh install, realistically, because there is so much customisation &c. on there and I'm fed up of having to reinstall ubuntu, I must have done it in excess of 20 times and it makes me wonder why I don't just use windows, hateful as it is, because I've never had to reinstall.

---

### Post by blueyelabs on 2008-11-01
Well, I solved it, on my own I might add... I don't know why no-one replied...

---

### Post by wakebdr on 2008-11-01
How did you solve it?  Please share so that you might help others in the same situation.

---

### Post by blueyelabs on 2008-11-04
Ok, here goes.

First I booted into "Recovery Mode". Now, for some reason, for me, internet wouldn't work from recovery mode so I had to start it going:

I first went into the root shell and typed:

```

ifconfig -a

```

which brought up only one connection (which was the loopback [127.0.0.1] connection).
I then had to try and setup the eth0 connection (I was using ethernet for this particular computer).
I tried to use:

```

ifup eth0

```

But I can't remember if this returned anything useful. I decided to try to setup eth0 properly since pinging my router gave me nothing:

```

ifconfig eth0 192.168.0.1

```

Where 192.168.0.1 was the local router address. That seemed to work, thankfully, so that I could then ping (but only when specifying eth0 as the interface).

I then used 

```

mii-tool eth0

```

Which gave me a good response (I'm afraid I can't really remember what it was, it said something like "link ok").
Finally, to get dhcp working, I used

```

dhclient eth0

```

I then tried pinging the router without specifying an interface, and it worked, so I exited the root shell and went back to the recovery mode screen.
I selected the dpkg option to fix all broken files, and it finally did its job and once I'd rebooted, everything worked like a dream.

I do apologise for the quality of this solution, because it was a good few days ago and I went through it all quite frantically. If you need any clarification just email me or something.

---

### Post by roxority on 2008-11-04
Thanks for posting this! What is "the dpkg option to fix all broken files"? I couldn't find that in "dpkg --help".

---

### Post by blueyelabs on 2008-11-05
It's in the recovery mode which you can access from grub. All these commands have to be accessed from recovery mode otherwise the networking stuff is pointless. So boot into recovery mode and then there should be a list of options like normal boot, dpkg something-or-other, root shell and xfix.
Don't use xfix whatever you do. First go into the root shell, then once you've done all that stuff then do the dpkg option.

---

