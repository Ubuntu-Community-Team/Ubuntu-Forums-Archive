---
title: "system login should not be qwerty"
date: 2023-03-24
forum: Installation &amp; Upgrades
---

### Post by seldontron on 2023-03-24
Hello,

I upgraded to 22.04.

I set it up for azerty (be) keyboard layout. But when I log out the system goes to qwerty, 
Once logged in everything goes as expected (azerty).

localectl 
   System Locale: LANG=en_US.UTF-8
                  LC_NUMERIC=en_GB.UTF-8
                  LC_TIME=en_GB.UTF-8
                  LC_MONETARY=en_GB.UTF-8
                  LC_PAPER=en_GB.UTF-8
                  LC_NAME=en_GB.UTF-8
                  LC_ADDRESS=en_GB.UTF-8
                  LC_TELEPHONE=en_GB.UTF-8
                  LC_MEASUREMENT=en_GB.UTF-8
                  LC_IDENTIFICATION=en_GB.UTF-8
       VC Keymap: be-latin1
      X11 Layout: be
       X11 Model: latitude
     X11 Variant: azerty

As you can see the system should be azerty.

kr,

---

### Post by seldontron on 2023-03-25
Found a way around it,

Everything seemed to be configured as needed, So I tried and switched 'Belgian' to  'Belgian ISO' (not knowing what the difference is).
For some reason the configuration was applied system wide after this.

```
 
sudo dpkg-reconfigure keyboard-configuration

```

Solved for now..

---

