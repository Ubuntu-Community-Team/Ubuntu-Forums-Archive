---
title: "Unity won't load on the admin profile"
date: 2014-04-19
forum: Installation &amp; Upgrades
---

### Post by theone4 on 2014-04-19
Oh lords of knowledge! I plead your assistance!

I upgraded to 14.04 and after the final reboot, I logged in the admin account but unity wont start so I have only the 14.04 background. no shortcuts work. I can login and use the guest and other accounts on the machine. I think i might have opted to keep one of the settings that I was asked to select during the upgrade to 14.04.

 I have only been using ubuntu since 13.04 so im not so familiar with it. my set up is dual boot with windows on a laptop. Can someone help ?

thanks a lot for your time

---

### Post by b-tainturier on 2014-05-05
Hello,

Did you try to delete the hidden folder ".config" ?

It solved this problem on my computer.

Here are the steps :
- open your session (so you only see the 14.04 background)
- open a terminal : [Ctrl] + [Alt] + [F1]
- delete the ".config" folder : ```
sudo rm .config -r
```
- reboot your computer : ```
sudo reboot
```

EDIT: actually deleting the folder .config is safe if you did a clean install of 14.04. If you upgraded from 13.10, you may lose config files (LibreOffice dictionnaries, Thunderbird mails,...). If you upgraded, you should save the folder .config before deleting it.

---

