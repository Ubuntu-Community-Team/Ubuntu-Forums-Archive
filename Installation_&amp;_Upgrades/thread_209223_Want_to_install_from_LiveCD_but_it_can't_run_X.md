---
title: "Want to install from LiveCD but it can't run X"
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by lapsey on 2006-07-04
I'm trying to install Dapper on a [Dimension 2350](http://support.dell.com/support/edocs/systems/dim2350/specs.htm)

Under normal install the system freezes when it launches X for the LiveCD environment: I get a background color filling the screen and a (unresponsive) mouse cursor.

When launched in safe graphics mode, it gives me a warning about how X is not properly configured. The term (tty2) this is displayed on also has some very strange behaviour when i entered a commant. But since I still have the other ttys I suppose it doesn't seem so important. 

The datasheet for this machine says it uses an integrated Intel Extreme 3d card, which according to google doesn't seem to pose a problem with linux.

So assuming this would be the best thing to do to see if i can even run X at all, how do i: kill the unresponsive x session on tty7, configure x.org and 'startx' into the LiveCD desktop environment?

---

### Post by taurus on 2006-07-04
Maybe you want to use the alternate CD version to install it.  Otherwise, try installing the server version and then install Gnome with
```

sudo apt-get install ubuntu-desktop

```
And if you ever need to configure your X again, do
```

sudo dpkg-reconfigure xserver-xorg

```

---

