---
title: "Dual boot Win/Ubuntu"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by Atlantix on 2010-01-28
I have recently added Ubuntu to a Windows box. The two systems co-exist peacefully, but...
 
At bootup, after the BIOS screens and the "Grub Loading" message I now have a list of several Linux options plus the Windows option at the very bottom. So if I turn the PC on and don't wait for this screen to load, it will automatically start Linux... 
 
How do I turn this list upside down so Windows is first? I know in Windows this is done under System Properties > Advanced > Startup and recovery > Settings > Default operating system... but I think that only refers to other Windows versions installed, Linux is not listed. I suppose I have to do it in Ubuntu, but how?
 
Thank you,

---

### Post by darkod on 2010-01-28
Write down the entry for windows in grub menu, exactly as it is, like "Windows 7 loader on (/dev/sda1)".
Boot ubuntu, in terminal open the file:
sudo gedit /etc/default/grub

In the line GRUB_DEFAULT=number change the value to the windows entry. This will make windows default choice regardless how many ubuntu kernels you have listed. If you want to change the timeout time (number of seconds it waits), change the value for GRUB_TIMEOUT.

Save and close the file. In terminal run:
sudo update-grub

for the update to be accepted in grub config file. That's it.

PS. Sorry, in the above I assumed you are using 9.10. In 9.04 and earlier it's different procedure.

---

