---
title: "OS doesn't boot correctly after install"
date: 2014-10-29
forum: Installation &amp; Upgrades
---

### Post by amanda8 on 2014-10-29
I just recently wiped my computer free of Win8 and installed Xubuntu 14.10. When I restart the computer most of the time the OS doesn't want to boot. I just get black screen, sometimes lit; but black, but sometimes not lit and black. Same thing happens when I completely shut down and then restart as well as in suspend mode... Not sure what I did, please help!

---

### Post by christopher9 on 2014-10-29
This may indicated a problem with your graphics card(s)....
Reinstall with the option for "Install third-party software" unchecked...this will install the plain-vanilla noveau graphics driver.  
If this is successsful, then you can install the correct drivers.

---

### Post by amanda8 on 2014-10-29
Can I install this graphics driver without completely re-installing the OS?

---

### Post by oldfred on 2014-10-29
If you can boot into system.

 # list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices
# or
ubuntu-drivers devices | grep recommended 

      
 #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root
What is installed
dkms status

---

### Post by amanda8 on 2014-11-02
> **oldfred said:**
> If you can boot into system.

 # list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices
# or
ubuntu-drivers devices | grep recommended 

      
 #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root
What is installed
dkms status


You've completely lost me.

---

### Post by oldfred on 2014-11-02
Can you boot live installer?
If so run the commands from a terminal, one at a time and post results. 
If longer text use code tags which are easy to add in advanced editor with the # icon in edit panel.

---

