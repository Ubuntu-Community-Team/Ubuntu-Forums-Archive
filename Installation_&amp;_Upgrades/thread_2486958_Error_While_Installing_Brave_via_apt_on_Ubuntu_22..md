---
title: "Error While Installing Brave via apt on Ubuntu 22.04"
date: 2023-05-17
forum: Installation &amp; Upgrades
---

### Post by oakenholly on 2023-05-17
[SIZE=3][COLOR=#000000][COLOR=#211F28][FONT=Poppins]**Disclaimer: I am very new to Linux**
I installed Brave via snap, but every time I launch it, it keeps asking me to make it the default browser when I already have done so. Because of that, I opted to try and install it via apt using the method given in this website: [https://brave.com/linux/](https://brave.com/linux/)[/FONT][/COLOR]
[/COLOR][/SIZE][COLOR=#211F28][FONT=Poppins][SIZE=3]However, upon trying to do so, I keep getting this error message in the terminal:[/SIZE]
[/FONT][/COLOR]
[COLOR=#211F28][FONT=Poppins][FONT=courier new]Invalid value set for option Signed-By regarding source [https://brave-browser-apt-release.s3.brave.com/](https://brave-browser-apt-release.s3.brave.com/) stable (not a fingerprint)
E: The list of sources could not be read.[/FONT]
[/FONT][/COLOR]
[SIZE=3][COLOR=#000000][COLOR=#211F28][FONT=Poppins]This also occurs when trying to install any other application via apt. Does anyone know why this happens, and does anyone have a solution? Thanks.[/FONT][/COLOR][/COLOR][/SIZE]

---

### Post by ne29914 on 2023-05-17
With me, it's either/or. You go with synaptic (apt) or snap for package management.
Using both at the same time is a mess.
Take your pick.

---

### Post by zebra2 on 2023-05-18
you can remove the snap version and install the deb version through the gnome software app.
 Edit: if you have a Brave installed from the snap store you can remove it with (sudo snap remove brave) . 

Or
You can remove the snap version and the install Brave from a terminal using the following process. 


sudo apt install apt-transport-https curl


sudo curl -fsSLo /usr/share/keyrings/brave-browser-archive-keyring.gpg [https://brave-browser-apt-release.s3.brave.com/brave-browser-archive-keyring.gpg](https://brave-browser-apt-release.s3.brave.com/brave-browser-archive-keyring.gpg)


echo "deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg arch=amd64] [https://brave-browser-apt-release.s3.brave.com/](https://brave-browser-apt-release.s3.brave.com/) stable main"|sudo tee /etc/apt/sources.list.d/brave-browser-release.list


sudo apt update


sudo apt install brave-browser

Note: Enter each command in the order given.  It will update your sources.list to provide Brave updates as they arrive.
          Line 1 will install curl which allows the key ring to install. 
          Lines 2 & 3 will setup your system for brave but will not give a visible response.

---

### Post by ardouronerous on 2023-05-21
Alternatively, you could just install Brave via Flathub: [https://flathub.org/apps/details/com.brave.Browser](https://flathub.org/apps/details/com.brave.Browser)

I have Brave installed through Flathub and it's working well.

---

