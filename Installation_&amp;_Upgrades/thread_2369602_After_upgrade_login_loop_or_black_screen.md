---
title: "After upgrade login loop or black screen"
date: 2017-08-24
forum: Installation &amp; Upgrades
---

### Post by Myst1234 on 2017-08-24
I've seen a lot of login loop questions and threads and have tried everything from here - 

[https://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop](https://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop)

What's strange is I am able to log into Unity 8 (via the dropdown from the icon in the login gui), although nothing seems to work in there, but the default ubuntu login just loops.

I've checked permissions, everything looks to be set to my username and group, I've moved and removed Xauthority, purged, reconfigured, reinstalled etc. lightdm, and more. I've been at this for a couple hours now and to make things worse my other computer's drive failed early this week so I am now stuck unable to get anything done.

I am able to login via tty (ctrl + alt + Fkeys), so I have been trying solution after solution via CLI for hours. If anyone can help me out here I will forever be in your debt. If there are links to questions or threads I may have not read yet feel free to drop them here, however I am pretty sure I've been through the majority and nothing has worked yet. 

I am running on an hp envy currently. 

Thanks in advance

EDIT:
I'm not sure if this helps but I noticed an error in the top right of the screen when trying to login - 

vboxclient: virtual box kernel not running. Exiting. 

Or something very close to that. I am not running ubuntu on virtual box, it is my only OS so it didn't make sense to me but may provide more info.

Output of ```
lspci -k | grep -EA3 'VGA|3D|Display'
```

    ```
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 520 (rev 07)
    Subsystem: Hewlett-Packard Company HD Graphics 520
    Kernel driver in use: i915
    Kernel modules: i915
```

I've checked ```
~/.xsession-errors
``` again and I see several 
```
dbus-update-activation-environment: setting
``` errors in there. This is over my head but does this help?

*Update*
After trying some more solutions I was almost able to install and run gnome. Unfortunately it was still throwing errors like crazy so I tried fixing some packages and things seemed to settle down. But then after reboot I am now brought to a black screen with a blinking cursor.

I've read in a thread that removing xorg seems to have worked for a couple people but have not tried that yet.

---

### Post by Myst1234 on 2017-08-25
No thoughts or ideas? Am i just screwed?
 I'm lost here and about to buy a flash drive to install a new OS with if there's nothing I can do.

---

### Post by ubfan1 on 2017-08-25
Can you login to the guest session?  If so, then the problem is in the "hidden" files (those starting with a dot) in your home directory.  These are used for configuration, and a mismatch will cause the sort of problems you have.  Login to a virtual terminal (you said they work), and make a directory tmpfiles in your home.  
mkdir tmpfiles
Then move the .cache directory to the tmpfiles directory so it will not be found at login.
mv .cache tmpfiles
  I suppose you could delete it, but then if you wanted something back, you would not be able to get it.
There are other directories like .config to try next if moving .cache does not fix the problem.

---

### Post by Myst1234 on 2017-08-26
There is no guest in my options anymore. Trying tmpfiles solution

---

### Post by Myst1234 on 2017-08-26
Doing that made some odd changes. My screen is now black and white, and zoomed in. But I was able to login so, little good little bad?

---

### Post by Myst1234 on 2017-08-26
I got some visible errors I can now fix.

---

