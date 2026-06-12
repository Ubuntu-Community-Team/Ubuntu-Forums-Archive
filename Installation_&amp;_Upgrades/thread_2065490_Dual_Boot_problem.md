---
title: "Dual Boot problem"
date: 2012-10-02
forum: Installation &amp; Upgrades
---

### Post by Hvidemose on 2012-10-02
I'm running dual boot for the first time. I changed the dual boot menu, so that Ubuntu is default. When i go to Ubuntu it makes an extra stop at the menu : **"GNU GRUB version 1,99-21 ubuntu3.4"**, where i have 3 options.

If i don't do anything within x-amount of seconds, it will automatically move on to Ubuntu, BUT how do i avoid this menu? It would be nice if i could just choose Ubuntu or Win 7, and then the startup would be normal.

---

### Post by darkod on 2012-10-02
By the sound of it, you installed wubi inside windows, not a dual boot.

Wubi is sort of a virtual ubuntu inside windows. The windows bootloader is still on the MBR and it adds entry for ubuntu. When you select ubuntu there, it boots the virtual wubi which has another bootloader on the virtual hdd. That is why you are seeing a second one.

If the above is correct, you can disable grub2 from wubi to detect the windows OS and add an entry for it by booting wubi, opening terminal and running:
```
sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub
```

That will disable the os-prober which searches for other OSs, and if it thinks only ubuntu is there it doesn't create the grub2 boot menu, it boots ubuntu right away. So that would eliminate the second boot menu.

Just make sure to remember this is NOT a dual boot in the true meaning of the term. And in future when you need help specify that you have wubi not ubuntu since some things are done differently and different commands need to be run.

---

### Post by Hvidemose on 2012-10-02
Ok interesting! i will look in to that.

But i actually fixed the problem this way:

> I used to use  startup manager, as pointed out by Chad--24216, but alas, it's no longer  being maintained, nor is it in the repositories.
It has been  superseded by "grub-customizer", which while up to date, is also not in  the standard repositories. To to add and install it simply do the  following at the terminal:
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
Press enter to confirm adding the PPA
sudo apt-get update
sudo apt-get install grub-customizer
Press Y to confirm
You  can now launch grub-customizer in the usual ways. If you ignore the  complete list you'll see when it first launches, and just press  "Preferences" button on the toolbar you'll get a nice summary dialog  where you can change the timeout value and default menu item, as shown  below:Grub Customizer preferences screen


a solution i found on this link: [http://askubuntu.com/questions/135113/how-to-change-the-time-for-os-selection-menu-in-grub](http://askubuntu.com/questions/135113/how-to-change-the-time-for-os-selection-menu-in-grub)

It was pretty simple [IMG]http://ubuntudanmark.dk/forum/images/smilies/ubuntu/icon_cool.png[/IMG] 

Thanks for inputs  [IMG]http://ubuntudanmark.dk/forum/images/smilies/ubuntu/icon_wink.png[/IMG]

---

