---
title: "Lucid Headless fileserver - can't VNC in w/out physical access first"
date: 2010-03-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by amp_man on 2010-03-26
I don't know if this was an issue in previous versions or not. I lost the OS drive in my fileserver (was running 8.04), so I upgraded it to Luicd when I dropped in the new one. It's supposed to be headless, but I'm having an issue where any time I reboot, I have to put in my password before I can VNC in. If I set it to auto-login, it prompts me for the password when attempting to VNC in, to access the keyring. If I log in manually, it doesn't do that, but I obviously have to log in at the physical computer. I'm using the included vino vnc server. Is this an issue on e.g. 9.10, or should I be reporting it as a bug? And if it's by design, how do I work around it?

Also, the other hard drives aren't automatically mounted at boot, they're detected but I have to mount them manually each time. I know I can just edit fstab, but is there a "better" (GUI) way to do it? I also have to recreate the shares every boot, which is getting annoying, I supposed I should just edit fstab and get it over with, but I've forgotten what all the options are to mount the ntfs drives properly, so that all users get rw access to them.

---

### Post by the yawner on 2010-03-26
For the VNC try searching on how to run vnc server at startup.

---

### Post by HermanAB on 2010-03-26
For heaven's sake, please don't use VNC.  Search these forums for tales of woe with VNC.

SSH works better, is easier to set up and it is secure.

---

### Post by stlsaint on 2010-03-26
I was just about to suggest ssh as i read herman's post. Yes SSH is MUCH better and you dont have to login physically to server before using ssh. At the terminal when using ssh syntax:
```
ssh <user>@server-ipaddress
```
you will be prompted with your specified authentication method be it username/password or keys. (I strongly suggest key authentication) but if you have password then you will be asked to provide it and then you will be at the prompt of your server.

---

### Post by spynappels on 2010-03-26
Also, are you running Lucid-Desktop or Lucid-Server? Have you installed a GUI if it is server?

---

### Post by KB1JWQ on 2010-03-26
If you are wedded to a GUI on a server, you can use x11 forwarding over SSH-- secure, and doesn't require a logged in user at the console.

---

### Post by amp_man on 2010-03-26
Wow, ask for tips on making hamburgers, and you get all the reasons hot dogs are better.

The system I'm VNC'ing in from is running windows 7, and VNC isn't exposed to the internet. I am running lucid-desktop. I have putty installed an know how to use ssh, but I rather like the ability to vnc in and look through a bunch of photos on the server, rather the load each one onto another computer over samba. I also have speakers hooked up to it, and use it to listen to Pandora or the music collection I have backed up on it. All I want to do is be able to log into it without getting into the closet to type in a password!

---

### Post by BwackNinja on 2010-03-26
This is just an access to the default keyring problem. It doesn't allow you to access it (because it uses the same password as your login) unless you have typed in your password before. There are workarounds for this, mostly known due to having this problem autologin with networkmanager.

[http://maketecheasier.com/auto-unlock-keyring-manager-in-ubuntu-intrepid/2009/03/14](http://maketecheasier.com/auto-unlock-keyring-manager-in-ubuntu-intrepid/2009/03/14) - this seems to be what you're looking for.

---

### Post by amp_man on 2010-03-27
Thanks for the info and the link, but I don't have the button in this step:

> Highlight the login – Automatically unlocked when user logs in entry. Press the Change Unlock Password button.

Please see the attached screenshots, they're from the main window (along with what I get if I click "Properties"), and the two Preferences screens. If I click on the e.g. "vino.local:5900" and then click properties I can view the stored password, but that's pretty much useless to me right now. Can someone tell me what I should do to auto-unlock the keyring?

---

### Post by BwackNinja on 2010-03-27
just right click that login thing that you have the properties for, and click "change password" and continue from that screen.

---

### Post by amp_man on 2010-03-27
> **BwackNinja said:**
> just right click that login thing that you have the properties for

I had tried that, but apparently right click doesn't work in my VNC session. Used the menu key, found "Change PW", all set now, thanks!

---

