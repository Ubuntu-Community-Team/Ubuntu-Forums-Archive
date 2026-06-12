---
title: "Installing Dropbox"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by pauloz on 2014-04-18
I'm having issues installing Dropbox on my netbook after upgrading to 14.04. I get a message "Nautilus Restart Required", then choose that option and then a message displays "Authentication is needed to run '/usr/bin/dropbox' as the super user". After I enter my password, nothing happens. I've never had any issues with Dropbox before. Can somebody help please?

---

### Post by kc1di on 2014-04-18
Hi Pauloz, 

How did you originally install dropbox?  from the software center or some other way?

You should install from the repositories nautilus-dropbox.  
for some reason it's requiring your root privileges to run that is not right. You should be able to run dropbox without root privileges.

did it create a dropbox folder in your home directory?

It runs perfectly here so lets see if we can find the problem.

---

### Post by pauloz on 2014-04-18
Hi Dave

I originally installed Dropbox from the Software Centre. I'm still learning about Ubuntu and I would need to get instructions how to install from the repositories nautilus-dropbox. No folder has been created in my home directory. 
I had no problems when I installed it on my desktop computer with Ubuntu 12.04 but I need to access Dropbox on my netbook.

Thanks
Paul

---

### Post by kc1di on 2014-04-18
I would uninstall what you done so far and install dropbox via the terminal.  Here's how to do it. 

in the terminal issue the following commands.
go to the software center and remove the one you installed first if you can.

```
sudo apt-get update
```
```
sudo apt-get install nautilus-dropbox
```

I would also install synaptic package manager I find it much easier personally than software center.
you can do that in the terminal but this command:
```
sudo apt-get install synaptic
```

Good luck and welcome to Ubuntu ;)

---

### Post by pauloz on 2014-04-18
Dave

I did what you instructed but as before, a window appears telling me to restart Nautilus, but nothing happens and after a couple of minutes the screen freezes completely. I switched off my netbook and when I rebooted, the Dropbox icon appeared in my task bar, however it can't connect to my Dropbox account. There's still no Dropbox folder in my home directory. I guess that's a little progress! 

PS: A few minutes later, I restarted my netbook and a message came up that my Dropbox folder was "missing". I chose the option to relink - it looks like we're up and running! Thanks for your time!

Paul

---

### Post by abrianb on 2014-04-18
I had the same Dropbox freeze issue on an upgrade to 14.04. On the second reboot I just clicked on the Dropbox icon in the panel, opened the folder and closed it. So far no more pop-ups asking to restart Nautilus or freezes.

---

### Post by bapoumba on 2014-04-18
Sometimes, I've had to run dropbox start from the terminal to have the icon appear in the panel.

---

### Post by kc1di on 2014-04-18
Hi Paul,
Glad you got it going.  I was going to suggest that you make the Dropbox folder , but sounds like it's all sorted , enjoy :)

---

### Post by waburden-4 on 2014-04-25
I'm having the same issues as those above after upgrading to 14.04, and  tried all the same solutions described. I'm not getting the Dropbox icon  in either the Unity bar or the system tray and nothing happens when I  try to launch the app other than the superuser authentication window  appears after a time. This is a gamechanger  app for me and if I can't  get it working I will rollback to 13.10.

---

