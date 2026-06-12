---
title: "blank screen after boot"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by puk on 2006-06-07
Hi,

I just did my first Linux install so bare with me - Right from the beginning there were severe "hickups" installing Ubuntu 6.06 Desktop. I have overcome the odd boot hangup : [http://www.ubuntuforums.org/showpost.php?p=1108534&postcount=49](http://www.ubuntuforums.org/showpost.php?p=1108534&postcount=49)

After booting all the way through the screen turned black - I am using a very old 12,1" LCD Screen. I know it can not adapt to other screen resolutions then its native 800x600 so I tried booting with a newer 17" screen and everything went fine but then I could not change the resolution to 800x600 and 60Hz, the x-server would restart over and over again.
So I tried booting with the 12" and plugging the 17" in when it turns black. That way I could log in and - surprise, surprise - now I was able to change the resolution and plug the 12" back in.

So everything is working smoothly exept for the Login-Screen that will still turn black on the 12" no matter what, so that I have to do a blind login and after that the desktop appears just fine.

...To make a long story short - I need help with this.

thank you.

---

### Post by firetux on 2006-06-07
Have a look [here]("http://www.ubuntuforums.org/showthread.php?t=190036&highlight=blank+screen")

Please report back if it worked.

---

### Post by WidowMkr on 2006-06-07
same problem here. It´s not your display... I have A64 3200+ with nvidia 2x6600gt SLI system with LG 1710s LCD monitor and can´t even install because I have no video when gdm start. (I hear the sound and the screen remains black)

---

### Post by puk on 2006-06-08
[QUOTE=firetux]Have a look [here]("http://www.ubuntuforums.org/showthread.php?t=190036&highlight=blank+screen")

Please report back if it worked.[/QUOTE]

Hi firetux,

that didn't work, but deleting any resolution higher than 800x600 in the section "Screen" did. Apparently the Login-Screen always uses the highest resolution given there no matter what you choose on the gnome desktop under System->Preferences->Screen Resolution

By the way I was not able to save the xorg.conf on Gnome I had to log out and do "ctrl+alt+f1" and do without the gui. Is there no sudo equivalent when working with the gui ?

---

### Post by puk on 2006-06-08
... oh, and thank you for your help firetux !

---

### Post by firetux on 2006-06-08
[QUOTE=puk]
By the way I was not able to save the xorg.conf on Gnome I had to log out and do "ctrl+alt+f1" and do without the gui. Is there no sudo equivalent when working with the gui ?[/QUOTE]

You can open the file in the terminal(sudo gedit nameoffile) or you could start nautilus with sudo nautilus, but I don't recommend that.

Tip: Tilda, you can find it in the repos and its basically a transparant terminal without borders, so you can always have th command line nearby.

>  	... oh, and thank you for your help firetux !
And thank you for posting a solution that could help a lot of people reading this tread!

---

