---
title: "How to recover password in Kubuntu/Ubuntu"
date: 2005-07-23
forum: Installation &amp; Upgrades
---

### Post by Dural on 2005-07-23
My brother and I reinstalled Kubuntu on another hard drive after we found out that the original hard drive had damaged sectors. After logging in to Kubuntu, we realized that in order to set up a wireless network connection and to set up Samba, we would have to know the sudo password. Unfortunately, neither of us could remember the sudo password we had chosen. How can a person recover/change their sudo password?

---

### Post by aggiechemist on 2005-07-23
First off, be sure you know what you mean when you say "sudo password." I forgot exactly how this works in Ubuntu, but many times sudo prompts you for a user password for the current user. I think what you are seeking may be more like the root password.

Root passwords can be changed in single user mode. To get there, reboot the computer. As it is booting, hit Esc to go into the grub menu. You will need to edit menu, specifically the line with the kernel command. You will need to add something to that line. I forget the exact thing to add, I belivee it is either the number 1 or the word single. Just append it after the kernel command and then press b to let Grub boot. If all goes well, the boot process wil continue normally for a while and then suddenly stop with you logged in as root. This is a way to make you root without ever entering a password. Then enter the command passwd and you can reset the root password. There is no way to recover the old password (sorry).

If what you need to do is to just change the password of a specific user instead, post again to lemme know and there is an even easier way.

Good luckl.

---

### Post by Dural on 2005-07-25
Ah, okay. So I guess the sudo password is only for basic login, but you still need the root to alter some settings. But if that's the case, isn't Ubuntu/Kubuntu supposed to be able to do that without using the root password?

---

### Post by majikstreet on 2005-07-25
The sudo password is the same password you login with.

Say your user account that you setup in the installer is jooj and the password is oop900
When you sudo in our example account here, your sudo password would be oop900

(Also, if you add another user and you want them to be able to sudo add them to the group wheel. If you want them to have full privledges like your original account, add them to the group admin.)

majikstreet




Also, if you can't login with your username for some reason (I had to do this, I didn't setup the password right for some reason), when you are booting after you see "Grub loading" hit F1 or F2 (I can't remember which one) and select the option that has the word "Recover" in it; you will be given full admin privledges.

---

### Post by Dural on 2005-07-25
Thanks for the help from both of you. I'm going to read more about the differences between root and sudo.

---

### Post by majikstreet on 2005-07-25
[QUOTE=Dural]Thanks for the help from both of you. I'm going to read more about the differences between root and sudo.[/QUOTE]
 You're very welcome.

---

