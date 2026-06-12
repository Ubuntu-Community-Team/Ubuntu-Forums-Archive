---
title: "Problems running apt-get -f install"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by adotei on 2007-05-08
Hi,
  I tried to install pidgin 2.0 on my ubuntu feisty box. However, it had dependencies problems thus I tried to install these required packages manually. They were fontconfig-config and fontconfig. 

I managed to do that but afterwards, I got an error message saying run sudo apt-get -f install to fix broken packages. I typed it out but to my surprise, it was going to uninstall my whole desktop packages to free about 2GB of space. All packages were going to be uninstalled. I can't remove the offending packages I installed manually too. 

Is there anything I can do to rectify this problem rather than reinstalling ubuntu? I have tried 
sudo dpkg --configure -a
but its still not working.

Thanks in advance,
Nii.

---

### Post by zvacet on 2007-05-09
**synaptic>edit>fix broken packages**

I hope it will help.

---

### Post by mlind on 2007-05-09
Does command "sudo aptitude install" offer you a solution that would solve the issue, preferably downgrading pidgin packages (it might not be the first suggestion). You should be able to solve the issue by removing installed pidgin packages. Try doing this using single remove/purge command, which usually makes apt more happy

For instance
```

sudo aptitude purge *package1 package2 package3* ..

```

---

### Post by adotei on 2007-05-09
Hi guys,
     thanks very much for the suggestions. They solved my problem. 

I typed "sudo aptitude install" and this identified the broken packages causing the problem. I was instructed to insert my Ubuntu Feisty Installation CD into the drive to recover the necessary packages to fix it.

All sorted in just one simple command. 

UBUNTU ROCKS BUT REMEMBER, ITS THE USERS THAT MAKE IT WHAT IT IS. THANKS FOR ALL YOUR HELP AND KEEP UP THE COMMUNITY SPIRIT.

Regards,
Nii-Adotei.

---

### Post by mlind on 2007-05-09
You can remove/comment out the cdrom entry from /etc/apt/sources.list if you'd rather use internet connection to fetch the packages. This way you don't have to have the Ubuntu cd in tray all the time. If you edit the file in question, remember to run "sudo aptitude update" afterwards.

---

