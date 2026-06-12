---
title: "low graphics mode crash"
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by jesse c on 2008-08-14
HELP!i was having trouble with google earth crashing while loading even though it worked for years.Ithought maybe my NVIDEA driver had auto updated to cause the problem so i went into synaptic and tried just about all the driver variations and managed to crash my Hardy OS.It now will only load in low graphics mode and it took several restarts just to get it to say my restricted driver(NVIDEA)was enabled but still wont come out of low graphics mode and my COMPIZ stuff wont work cause it now tells me my graphics card wont allow the advanced graphic setting Where do i start to fix? im thinking some part of a synaptic package is missing  but i have reloaded what i think was the original working package but most of the nvidea packages indicate they work for my GEFORCE 6150LE card

---

### Post by timkoop on 2008-08-15
I don't know much about Google Earth or Compiz, but I've played around with Nvidia cards a bit.

Try running:
sudo nvidia-settings

This will bring up Nvidia's display settings manager thing, which is actually quite intelligent. Note: you must actually run it with "sudo"; don't actually run it as root.  Once the window comes up, find the button "Save Xconfig File", or something like that, and do it.  If the window doesn't actually come up in the first place, it could be because you have the wrong driver chosen (i.e. not Nvidia's restricted driver).  It should tell you what to run to fix that.  (I think it is another nvidia-??? command)

If this command can't be found, install it like this:
apt-get install nvidia-settings.

You might need to reboot your X-server.  Either log out or hit Ctrl-Alt-Backspace.  You don't need to do a full reboot when playing with the X-server.

--
Tim

---

### Post by jesse c on 2008-08-15
thanks TIM i tried those methods and it still wont come out of low graphics and for kicks i loged onto google earth and it tells me im running with no graphics card enabled and when i check my system setting sometimes it says my restricted driver is enabled and sometimes it isnt and i chek the "enable" box and reboot but no visible graphic changes also i cant change my monitor profile above 800/640 cause it only gives me two choices this was true when i first loaded ubuntu and didnt know about enabling the restricted drivers When i tried to chek my xconfig in terminal it asked for root password which i never set and dont know

---

### Post by timkoop on 2008-08-15
> **jesse c said:**
> i cant change my monitor profile above 800/640 cause it only gives me two choices

Where are you trying to make this change?  Try changing it in Nvidia's settings window by running "sudo nvidia-settings".

---

### Post by jesse c on 2008-08-15
ive tried the sudo nvidia settings approach with no luck,but i did notice that when clicked on "settings/administration/x config settings"it shows a pop up warning box that says my system needs my x server restarted and prompts me to edit my x config fileby "just run'nvidia-xconfig'as root".How do i run as root?I tried "sudo nvidia-xconfig" but it doesnt bring up any kind of settings option but tells me a new x config file written to '/etc/x11/xorg.conf' does that give any clues?

---

### Post by timkoop on 2008-08-18
> **jesse c said:**
> ive tried the sudo nvidia settings approach with no luck,but i did notice that when clicked on "settings/administration/x config settings"it shows a pop up warning box that says my system needs my x server restarted and prompts me to edit my x config fileby "just run'nvidia-xconfig'as root".How do i run as root?I tried "sudo nvidia-xconfig" but it doesnt bring up any kind of settings option but tells me a new x config file written to '/etc/x11/xorg.conf' does that give any clues?

Yes, that makes sense.  When you run 'sudo nvidia-xconfig', that changes your xorg.conf file to use Nvidia's proprietary driver.  That is good.  In fact, that change may have been all you needed.  But now you can restart and run "sudo nvidia-settings", then click the "save to xorg.conf file" button.  That is also a good thing to do.

---

### Post by offchance on 2008-08-19
I have done all of this and it does not work. still stuck in low graphics mode (even when I use envy instead of hardware drivers).

---

