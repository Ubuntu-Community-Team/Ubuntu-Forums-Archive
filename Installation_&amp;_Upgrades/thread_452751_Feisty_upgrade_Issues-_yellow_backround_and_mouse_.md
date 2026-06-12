---
title: "Feisty upgrade Issues- yellow backround and mouse only after login"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by Magicalturkey on 2007-05-23
I upgraded to feisty. it crashed during installation, i got it going again, and once it was done it rebooted, and once it starts up again i can log in but i am unable to go much further. 

Once i log in it goes to the yellow backround and gives me my mouse, but the system does not load.  

Is there anyway to diagnose it? or where is a good place to start. 

I chose and tried all the other options in the boot menu with the same results

Thanks.

---

### Post by Magicalturkey on 2007-05-23
update: so i was able to get in using the GNOME start up without loading any startup processes. I then tried to run the update manager again and got these errors. 
i'm not totally sure what they mean, or what i need to do to fix it. 

Could not install 'acpid'
upgrade aborts now. Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.
"subprocess post-installation script returned error exit status 1"

Could not install 'acpi-support'

The upgrade aborts now. Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.
"dependency problems - leaving unconfigured"

Could not install 'powermanagement-interface'

The upgrade aborts now. Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.
dependency problems - leaving unconfigured

Could not install 'gnome-power-manager'

The upgrade aborts now. Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.
dependency problems - leaving unconfigured

Could not install 'gnome-session'

The upgrade aborts now. Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.
dependency problems - leaving unconfigured

Could not install 'ubuntu-desktop'

The upgrade aborts now. Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.
dependency problems - leaving unconfigured

---

### Post by Magicalturkey on 2007-05-24
ahh hah! 
I figured out the solution to these issues. 
I booted into the recovery module, and ran sudo apt-get -f install.  and it was able to fix the dependencies and fix all the errors. 

For some reason it was unable to fix using the same method when in the normal gui enabled interface.  
however its fixed 

VICTORY!

---

