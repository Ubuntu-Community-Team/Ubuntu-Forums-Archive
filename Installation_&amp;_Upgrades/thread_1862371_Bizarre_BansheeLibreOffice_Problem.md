---
title: "Bizarre Banshee/LibreOffice Problem"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by haon8 on 2011-10-16
Hello, my father is using Ubuntu and upgraded from 11.04 to 11.10 earlier today. I'm currently at school, so wasn't able to help him with it (he's fairly slow when it comes to computers, he's been around for many decades), but I told him that it would be fairly self-explanatory. It went well, but he told me about a bizarre problem he's having with Banshee opening when it isn't supposed to. He says that a number of files and folders are linked to the Banshee program (such as Recycle Bin, whenever he plugs in a flash drive), and that when he tries to open them, it instead opens Banshee. Each of the shortcuts that are associated with Banshee (that shouldn't be) have the Banshee logo on it, however my dad says that when he right-clicks on the shortcut, it brings up options that are associated with the shortcut is actually supposed to be. As an example, if he right-clicks on the Recycle Bin shortcut, it brings up an option to empty the recycle bin, however the shortcut still looks like the Banshee logo and when clicked on it brings up Banshee. Similarly, when plugging in a flash drive, he can right-click on it to safely remove (among other things), but it still opens Banshee when clicked on. It's possible that this is a glitch in the system, but also very possible that he accidentally did something which changed file associations.

He also has a (what I believe to be separate) problem where if he tries opening an existing word file with LibreOffice, the buttons don't appear in the upper-left corner to exit out of, minimize, or switch between window mode/fullscreen. However, he says that if he opens a new file, those buttons are there.

Either way, any help with these problems would be appreciated. Thanks!

---

### Post by haon8 on 2011-10-16
Anybody?

---

### Post by Serious_Python on 2011-10-17
Have you tried asking him to remove the Banshee and Libreoffice packages and then re-installing them?

I had a similar issue with flash and just used sudo apt-get remove to remove and re-install

---

### Post by haon8 on 2011-10-17
Thanks, I'll tell him to try that. Just out of curiosity, what's the easiest way to uninstall programs on 11.10? On 11.04 we'd go to the Software Center, search for the program and uninstall it. Is there a list somewhere that shows all of the installed programs?

Additionally, as silly as this question may be, where is the volume control on 11.10? My dad says that it's not in the upper-right corner like it used to be, and I haven't been able to find anything. Normally these issues would be easy to solve, but I use Windows and since I'm not at home it's difficult to try troubleshooting over the phone.

---

### Post by Serious_Python on 2011-10-18
> **haon8 said:**
> Thanks, I'll tell him to try that. Just out of curiosity, what's the easiest way to uninstall programs on 11.10? On 11.04 we'd go to the Software Center, search for the program and uninstall it. Is there a list somewhere that shows all of the installed programs?

Additionally, as silly as this question may be, where is the volume control on 11.10? My dad says that it's not in the upper-right corner like it used to be, and I haven't been able to find anything. Normally these issues would be easy to solve, but I use Windows and since I'm not at home it's difficult to try troubleshooting over the phone.

I must say I haven't really noticed where the uninstall list sits but I'll look it up. I usually use the sudo apt-get remove. It just seems to work a lot better, if you are paranoid and want to make sure all the bits and pieces are removed you can do an "sudo apt-get purge".

With regards to supporting your dad I would look into Teamviewer. It is free for personal use, it is secure and it lets you take control of your dad's machine from a variety of platforms (Windows, iOS, Android, Linux) Check out the product on their website, download it and install on both machines and then you can take a look at his machine wherever you are yourself.

---

### Post by Serious_Python on 2011-10-18
So in Ubuntu Software Center there is now a tab at the top called "Installed". under that tab all your apps are listed by category. You can then use that list to select an App and two buttons appear. "More Info" and "Remove".

With regards to the volume control check that your sound settings are correct. It is in the same place next to the clock on my installation.

---

### Post by haon8 on 2011-10-18
Thanks for the help python, we might try Teamviewer later.

Most of the problems seem to be solved, including the issue with opening Recycle Bin/flash drive (by uninstalling Banshee and Movie player, the latter of which came up when trying to open the Recycle Bin/flash drive when Banshee was uninstalled) and the issue with there being no buttons in the upper-left of LibreOffice (fixed by re-installing the program). However, the issue with the sound control still remains. Despite the fact that sound on the system does work, there's still no volume control present in the upper-right where there should be. I've read that this can happen when Banshee is uninstalled, however according to my dad it's still not there even when Banshee is installed. I'll have him check the sound settings under System Preferences when I talk to him later.

Additionally, he's been having an issue listening to radio stations online (foreign stations). On 11.04, he had the links under his favorites, and he just had to open them. After a few seconds they'd start playing with Banshee. For some reason with 11.10, it won't play with Banshee, and when it prompts to install the VLC plugin for radio station playing it won't work. Either way, this is a fairly minor issue that I'm sure could be caused by many things, so you guys don't need to worry about it. I'm sure I can figure it out with Teamviewer.

---

### Post by coachwhip on 2011-10-19
Actually I have had the banshee problem, will remove and reinstall it now to see if it is any better.

** Removed Banshee and it will now open file manager again. Not tried to reinstall yet, but I don't like banshee anyway **

---

