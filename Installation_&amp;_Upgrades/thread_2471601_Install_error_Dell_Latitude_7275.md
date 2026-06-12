---
title: "Install error Dell Latitude 7275"
date: 2022-02-03
forum: Installation &amp; Upgrades
---

### Post by John Jason Jordan on 2022-02-03
I just bought a Dell Latitude 7275 2-in-1 computer and I'm trying to install Xubuntu. I started with 21.10, which runs fine, touchscreen and wifi working, but then I discovered that it doesn't auto-rotate the screen. This is unacceptable, because my whole purpose for this computer is to use it to read books and journal articles. I found a post about four weeks ago here from a user who had the same problem, but he had originally installed 20.04, where auto-rotate worked fine. So I decided to go with 20.04.2. I burned the image to a USB stick and got it booted up, but when I click on the 'Install Xubuntu 20.04.2.0 LTS' icon the light on the USB drive flickers for a few moments, and then nothing happens. 

To troubleshoot I right-clicked on the icon and from its Properties I copied the command 'sudo --preserve-env-DBUS_SESSION_BUS_ADDRESS,XDG_DIR sh -c 'ubiquity gtk_ui.' Then I pasted it into a terminal, which gave me 22 lines, ending in 'OSError: [Errno 5] Input/output error: 'var/log/installer' .'

The computer came with Windows 10 on a 256GB SSD, still installed, but I planned to nuke it, and later install it in Virtualbox. Auto-rotate works fine in Windows, so the sensors must be working.

I need some ideas. :(

---

### Post by MAFoElffen on 2022-02-04
When it is running in the liveCD session, go to the UbuntuForums 'system-info' link in my signature line and run the script to create a system information report... When it get to upload the report to a pastebun, say (y)es, and copy the link to post here.

That way we get a better picture of what (X)ubuntu sees as hardware, and what drivers it is using or not, for that hardware. What I suspect, is that it needs to use at tablet type of rotation driver, which is not being loaded, or is not configured right... So is not seeing the sense change when it occurs.

---

### Post by John Jason Jordan on 2022-02-04
@MAFoElffen:
Thanks for the comment. I have made progress. It took a looooong time, but I finally got 20.04.2 installed and sort of working. The reason it took forever was UEFI and Windows. I just couldn't get it to stop automatically booting to Windows. I would shut down, boot, and hold down F12, and that would show the Windows on the main drive and the USB stick with Xubuntu. I'd select Xubuntu, and then it would boot to Windows. Only late last night I finally got it to start Xubuntu, and the Grub menu had 'Install Xubuntu' as an option. This allowed me to bypass the icon on the desktop that wouldn't work. And the install routines brought up the main drive, so with great glee I nuked all the Windows crap and installed new partitions for / and /home using the entire disk. It's not going to boot Windows now!

Touchscreen and wifi are working. I have a lot of apps to install and configs left to fix, but the big issue that I can't seem to solve is the screen auto-rotate. I'm going to start a new thread on that issue and mark this one solved, although I didn't actually solve the problem with the Install icon failing.

---

### Post by MAFoElffen on 2022-02-04
Post back here, where you open that new thread... So I can get to it.

I didn't find an actual "autorotate feature" that is already within Ubuntu or it's flavors... but I did find some things where I can read the screen rotation sensor... Where I have some ideas for some scripts to be able to change that based on what the sensor sees... Maybe if I get that going for you, that we can recommend/propose that as an improvement/addition for Ubuntu.

Manually, if you go to Settings > Display > Screen Rotation... You can change it there.

---

### Post by MAFoElffen on 2022-02-04
I found a GUI app to easily and quickly change that
```

sudo apt install arandr

```

---

### Post by John Jason Jordan on 2022-02-04
> **MAFoElffen said:**
> I found a GUI app to easily and quickly change that
```

sudo apt install arandr
```

Thanks!

It may work, but I can't figure out how to use it. No documentation, and the screen shows one thing called 'eDP-1.' What the heck does that mean? There's an image with a + on it, but when I click on it nothing happens.

Edit: I succeeded in creating a new one to rotate 90 degrees to the right. Then I figured out that, with the new one in front in the window, you click on the green arrow - and it worked!

But then I wanted to go back to landscape, and when I tried it I got an error message that there was no such definition, and did I want to go ahead anyway. I didn't have any choice, so I said Yes, and next thing I was staring at a completely black display. Ctrl-Alt-F2 got me terminal, but the only thing I could think of was 'sudo reboot.' 

I am thinking that it might be simpler just to study out xrandr, then write a command to go right-screen and another for back-to-landscape, put each in a bash script, give each an icon, and park them in the panel.

---

### Post by MAFoElffen on 2022-02-05
Like these:
```

xrandr --output eDP1 --rotate normal && gsettings set com.canonical.Unity.Launcher launcher-position Left
xrandr --output eDP1 --rotate inverted && gsettings set com.canonical.Unity.Launcher launcher-position Left
xrandr --output eDP1 --rotate right && gsettings set com.canonical.Unity.Launcher launcher-position Bottom
xrandr --output eDP1 --rotate left && gsettings set com.canonical.Unity.Launcher launcher-position Bottom

```
I'm looking up the same and other commands in gsettings... Like I said, I could make a script that looks at changes to monitor-sensor orientation... but I know that that can also be a bit buggy. That is why autorotate was removed just after 18.04.

---

