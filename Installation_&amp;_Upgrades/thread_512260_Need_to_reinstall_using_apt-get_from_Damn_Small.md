---
title: "Need to reinstall using apt-get from Damn Small"
date: 2007-07-29
forum: Installation &amp; Upgrades
---

### Post by roachk71 on 2007-07-29
Well, it finally happened: My CD-RW drive crashed entirely, leaving me with only Damn Small Linux. :(

Not to put DSL down, it's a darned good idea for small and embedded systems, but I would like to reinstall Xubuntu using apt-get from DSL, since I can't afford a new drive for at least a couple of months.

I need to know whether or not the primitive apt system for DSL can help me in performing this action across the 'Net, and what (if any) special procedures need to be used.

I would be most grateful for any assistance.

Thanks :KS

---

### Post by roachk71 on 2007-07-29
Bump: Anybody?

---

### Post by jim_p on 2007-07-29
You can try this:

[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

or this:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) 

if your pc supports booting from usb.

---

### Post by roachk71 on 2007-07-29
Unfortunately, neither of these methods would work in this situation; I can't use GParted since it can't be installed. I could use PartEd, but would have to unmount my working partition (again not an option, since I have no access to external boot media...Certainly not any large enough for the procedure.)

I'm also no expert in setting up a TFTP session on Dad's Windows machine.

What I do have access to is DSL's version of the APT tools and dpkg: These would be the best choice (if I had a good enough sources.list file with the appropriate repository keys, if any.)


If anybody out there can at least point me to where I can find this information, it would be a sanity-saver.  ](*,)

---

### Post by roachk71 on 2007-07-30
Never mind...

This apparently can't be done safely from Damn Small, since the necessary apt upgrade would probably break the entire system!

Thanks anyway... :-k

---

