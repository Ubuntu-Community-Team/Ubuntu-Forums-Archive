---
title: "&quot;please exit X before installing&quot;"
date: 2005-07-12
forum: Installation &amp; Upgrades
---

### Post by cinematography on 2005-07-12
Here is the error message I got when I tried to install the nvidia driver: 

"ERROR: You appear to be running an X server; please exit X before installing.  For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at www.nvidia.com."

How do I "exit X, or start the installation without "X? Whatever the hell "X" is. :(

---

### Post by varunus on 2005-07-12
Are you trying to install a custom nvidia driver?  You can get one from synaptic.  To shutdown your X server, hit CTRL-ALT-F1, log in at the prompt, and type
```
sudo /etc/init.d/gdm stop
```

This quits X, the basis for linux GUI's.  Then run the nvidia setup program from your console.  To start X (and GNOME) again, type:

```
sudo /etc/init.d/gdm start
```

However, you should be able to get the nvidia drivers from synaptic.  Look for a howto in the tips and tricks section.

---

### Post by cinematography on 2005-07-12
[QUOTE=varunus]Are you trying to install a custom nvidia driver?  You can get one from synaptic.  To shutdown your X server, hit CTRL-ALT-F1, log in at the prompt, and type
```
sudo /etc/init.d/gdm stop
```

This quits X, the basis for linux GUI's.  Then run the nvidia setup program from your console.  To start X (and GNOME) again, type:

```
sudo /etc/init.d/gdm start
```

However, you should be able to get the nvidia drivers from synaptic.  Look for a howto in the tips and tricks section.[/QUOTE]
You were right... [http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

And that was almost too easy. :D Thanks a lot.

---

