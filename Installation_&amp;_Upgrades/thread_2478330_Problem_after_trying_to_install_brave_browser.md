---
title: "Problem after trying to install brave browser"
date: 2022-08-23
forum: Installation &amp; Upgrades
---

### Post by rishi-jpg on 2022-08-23
I tried installing the brave browser using following commands in the terminal 

sudo apt install apt-transport-https curl

sudo curl -fsSLo /usr/share/keyrings/brave-browser-archive-keyring.gpg [https://brave-browser-apt-release.s3.brave.com/brave-browser-archive-keyring.gpg](https://brave-browser-apt-release.s3.brave.com/brave-browser-archive-keyring.gpg)

echo "deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg arch=amd64] [https://brave-browser-apt-release.s3.brave.com/](https://brave-browser-apt-release.s3.brave.com/) stable main"|sudo tee /etc/apt/sources.list.d/brave-browser-release.list

sudo apt update

sudo apt install brave-browser

and after doing so, this error came up, I have attached the screenshot of the problem. 

Thank you peeps.

---

### Post by mIk3_08 on 2022-08-24
> **rishi-jpg said:**
> I tried installing the brave browser using following commands in the terminal 

sudo apt install apt-transport-https curl

sudo curl -fsSLo /usr/share/keyrings/brave-browser-archive-keyring.gpg [https://brave-browser-apt-release.s3.brave.com/brave-browser-archive-keyring.gpg](https://brave-browser-apt-release.s3.brave.com/brave-browser-archive-keyring.gpg)

echo "deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg arch=amd64] [https://brave-browser-apt-release.s3.brave.com/](https://brave-browser-apt-release.s3.brave.com/) stable main"|sudo tee /etc/apt/sources.list.d/brave-browser-release.list

sudo apt update

sudo apt install brave-browser

and after doing so, this error came up, I have attached the screenshot of the problem. 

Thank you peeps.
You have unmet unmet dependencies. Please install all the unmet dependencies. Regards and cheers
```
sudo apt install <package or unmet dependencies>
```

---

### Post by deadflowr on 2022-08-24
The problem is the entry somehow added a quote to it so it reads as "deb,
which is not acceptable.

You can either delete the created file
```
sudo rm /etc/apt/sources.list.d/brave-browser-release.list
```
and try the echo command again.
Or open the file in an editor and remove the offending quotes.
```
sudoedit /etc/apt/sources.list.d/brave-browser-release.list
```
Note that sudoedit will use whatever the set editor is,
in Ubuntu the default is the nano editor.

Some nano editor basics here: [https://linuxize.com/post/how-to-use-nano-text-editor/]("https://linuxize.com/post/how-to-use-nano-text-editor/")

If you want to run with a different editor you can follow the answer found here: [https://askubuntu.com/questions/454649/how-can-i-change-the-default-editor-of-the-sudoedit-command-to-be-vim]("https://askubuntu.com/questions/454649/how-can-i-change-the-default-editor-of-the-sudoedit-command-to-be-vim")

---

### Post by Cavsfan on 2022-08-27
I use Brave quite a bit; my new favorite browser. I installed it on Xubuntu 22.04 from [[COLOR=blue]here[/COLOR]]("https://brave.com/linux/#release-channel-installation") recently.
I also use it on Arch, Fedora, Windows 10 and my Android phone.

---

