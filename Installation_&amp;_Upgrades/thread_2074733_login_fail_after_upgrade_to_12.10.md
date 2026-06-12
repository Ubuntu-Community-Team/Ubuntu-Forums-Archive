---
title: "login fail after upgrade to 12.10"
date: 2012-10-22
forum: Installation &amp; Upgrades
---

### Post by mitsumits on 2012-10-22
After the upgrade reboot I get stuck in log in screen.
Tried Ctrl+Alt+F1, loged in as an administrator user, typed:
sudo service lightdm stop
and I got stop: Unknown instance:

I was trying to use the following commands that promised to solve my login problem:

sudo service lightdm stop
sudo mv $HOME/.Xauthority $HOME/.Xauthority.backup
sudo service lightdm start

Please help. What can I do to find what's wrong?

---

### Post by buckyaustin on 2012-10-22
Try "sudo apt-get autoremove", "sudo apt-get autoclean", "sudo apt-get clean".
After all that try, "sudo apt-get update --fix-missing". Then "sudo apt-get update". Then "sudo apt-get upgrade". Then "sudo apt-get dist-upgrade".

This is to check if the update process went to plan. Tell us if there is an error when doing this. The repsotories have been a problem for me lately updates are getting half done, causing errors but running these commands over and over eventually I get all the updates.

---

### Post by mitsumits on 2012-10-22
Thanks but no luck.
Didn't have any errors and still have the same behaviour.
When I boot, I see Guest and AdminUser.
When I choose guest, there is a blink and back to the login screen.
When I choose adin, the admin username floats, with no place to type password and I can't do anything from there, apart from Ctrl+Alt+Del

---

### Post by buckyaustin on 2012-10-22
You could try reinstalling lightDM. This should get lightDM to the correct settings. Restart and check again. Another solution would be to install Kubuntu or any other. This will give you an alternative to lightDM. This should allow you to log in then.

---

### Post by mitsumits on 2012-10-22
Kubuntu was installed on this pc.
I did the upgrade though from unity 12.04


LightDM has the default values that I saw from [http://askubuntu.com/questions/74196/how-to-restore-lightdm-settings](http://askubuntu.com/questions/74196/how-to-restore-lightdm-settings)

How should I try installing Kubuntu? As I said Kubuntu 12.04 was on the pc before the upgrade.

---

### Post by buckyaustin on 2012-10-23
That means Kubuntu has been updated too. That is were your conflict seems to be. Which Ubuntu distro's did you have installed before hand?

We need to know this because each Distro' will use different programs to do the same thing and can conflict. This usually happens after upgrades. 

Remember before each upgrade please back up.

---

### Post by mitsumits on 2012-10-23
I had the previous version 12.04
I have a few data that were not backed up, so I'd prefer a solution that does not involve a fresh install, if possible...

---

### Post by topler on 2012-12-12
I had the same issue. After entering the password at the login screen I only saw some flickering and was then presented again with the login screen. I then found this post where it suggested to re-install lightdm.

I then removed lightdm and tested again without installing it again and I then was able to login successfully.
GDM is used now, which comes with a prettier login screen!

In my case, lightdm was installed a couple of years back and was dragged on by every Ubuntu upgrade. In my case, lightdm is obsolete and thus having it removed is a perfect solution for me.

---

