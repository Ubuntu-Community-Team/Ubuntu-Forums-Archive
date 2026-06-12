---
title: "Ubuntu reinstallation from live cd problem."
date: 2017-04-10
forum: Installation &amp; Upgrades
---

### Post by auteur on 2017-04-10
I had been running Ubuntu 12.04 for a year or so until I recently decided to upgrade to 14 and then 16 a week later.  I was fine in 14 and should have left well enough alone.  When I upgraded to 16 I received a "Low Graphics Mode" message suggesting I would need to configure my graphics card and input devices myself.  I attempted rebooting, and was prompted to enter a password.  I removed the psswd jumper on my old gx280 motherboard, then rebooted.  I kept getting the same "low Graphics Mode" message so I decided to do a reinstall from a live cd to a much older version and upgrade from there.  The reinstall appears to have worked but now I am prompted to enter a passphrase and password, so essentially I am back where I started.  

I would very much appreciate feedback as to how to restore my OS, and/or how to get the "Low Graphics Mode" message back and how to reconfigure (if this is an appropriate fix).   I can access the bios, and have been reading the Linux Bible, but beyond this I am stuck.    

Thanks in advance to the forum for your help.

---

### Post by RobGoss on 2017-04-10
Hello and welcome, Please see this post here it has some good information on the** low graphic mode** [http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error](http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error)

Do you get the low graphic mode when you try installing 16.04.2?

---

### Post by mörgæs on 2017-04-11
Please copy the command ```
sudo lshw -sanitize > lshw.txt
``` and paste it to the prompt, run it and post the resulting lshw.txt in CODE tags. It will tell us your hardware details.

---

### Post by auteur on 2017-04-18
Thanks RobGoss.  
I have read some of the posts you suggested and have copied the commands including "sudo apt-get install --reinstall ubuntu - desktp sudo reboot"  and "sudo apt-get autoclean" then "sudo du-sc/*/*lsort-g" to delete unwanted large file content.  I'm headed home to give these a try.  

Sincerely, Auteur.

---

### Post by auteur on 2017-04-18
Thanks, Morgaes.  I'll  give this a try.  

Sincerely, Auteur.

---

