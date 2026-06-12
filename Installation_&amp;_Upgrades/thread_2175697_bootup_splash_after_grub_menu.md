---
title: "bootup splash after grub menu"
date: 2013-09-20
forum: Installation &amp; Upgrades
---

### Post by jamzen on 2013-09-20
Running 12.04, religiously updated -- and sometime in the past several months, the bootup splash lost its usual neat five-dot progress screen.  What I get now is a crudely lettered FOUR-DOT progress screen, preceded and followed by a couple of error messages that flash by too quickly to write down.

But then I get my regular desktop, operating flawlessly.

Obviously, this is not a show-stopper.  But it is irritating, and I'd like to know what's going on here, and what I can do about it.  Go ahead, be technical.

---

### Post by Kirboosy on 2013-09-20
Maybe try this?

[How to Change the Splash Screen]("http://askubuntu.com/questions/228041/how-to-change-the-splash-screen")
```
sudo update-alternatives --config default.plymouth

sudo update-initramfs -u
```

Maybe just reselcting the theme will straighten it out.

Best of luck!
~Caboose

---

### Post by jamzen on 2013-09-20
Thanks, but nothing's changed.  The 'update-alternatives' tool responded with this:
      There is only one alternative in link group default.plymouth: /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth
      Nothing to configure.

And so, unsurprisingly, the only effect of 'update-initramfs -u' was to revise the timestamp on
      -rw-r--r-- 1 root root 14247266 Sep 20 15:32 initrd.img-3.2.0-53-generic

And the reboot behavior is unchanged.

Weirdness.  I've seen that four-dot progress bar occasionally before but never kept track of the circumstances.  Has anybody else observed or noted it?

---

