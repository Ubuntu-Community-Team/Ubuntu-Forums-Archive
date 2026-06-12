---
title: "Keyboard and Mouse only work in Recovery Mode Ubuntu 16.04 LTS"
date: 2016-10-28
forum: Installation &amp; Upgrades
---

### Post by isulaiman on 2016-10-28
This is a cross post:

  I just got an Intel NUC Kit NUC5PGYH.  It has 8GB of RAM and a 500GB HDD.  


  **The Problem**

  For the last week I've been trying to install Ubuntu 16.04 LTS from a  USB drive.  Each time I'm able to successfully install the OS. However,  when I load the OS, once I get to the GUI my mouse and keyboard stop  working.  There is power coming to the mouse at least (As I can see the  red light from the bottom of the mouse). 
  The keyboard and mouse both work in the BIOS settings and startup of  the computer, and work during the installation process.  Additionally,  if i load ubuntu in recovery mode the keyboard and mouse work!!


  **What I've Tried**
  
[LIST]
[*]I've tried using different USB ports and even a USB hub, both made no difference. 
[*]I've tried loading older kernels (not in recovery), again the keyboard and mouse don't work. 
[*]I've loaded  Ubuntu in recovery mode, and run sudo apt-get update && sudo apt-get upgrade successfully.  I also updated my Intel Graphics Card Drivers. However, still when I reboot the system the keyboard and mouse don't work. 
[*]I've made sure my BIOS has USB Legacy Support On, still with no change. 
[*]I've edited my grub.conf file (based on other suggestions) to turn on iommu, GRUB_CMDLINE_LINUX="iommu=soft", still no change. 
[*]I've run a boot repair, again with no change. 
[/LIST]
  
If anyone has any suggestions or advice I'd really appreciate it, I don't know what else to do!!

  
Thank you in advance

---

