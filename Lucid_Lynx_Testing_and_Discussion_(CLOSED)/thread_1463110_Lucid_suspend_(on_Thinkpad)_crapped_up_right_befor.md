---
title: "Lucid suspend (on Thinkpad) crapped up right before release ... again"
date: 2010-04-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jwbaker on 2010-04-26
Same story as the last 5 million Ubuntu releases.  Everything works fine right up until the RC, whereupon everything falls to pieces.  Right now my ThinkPad X61 doesn't suspend when I close the lid, and doesn't suspend when I use the suspend key (Fn+F4).  Was working fine right up until the RC.

---

### Post by LKjell on 2010-04-26
What video driver are you using?

---

### Post by jwbaker on 2010-04-26
I'm wearing black underpants.  Does that seem relevant?  No?  Neither is the video driver relevant to whether the ACPI subsystem responds to lid close and keypress events.

---

### Post by timosha on 2010-04-26
> **jwbaker said:**
> I'm wearing black underpants.  Does that seem relevant?  No?  Neither is the video driver relevant to whether the ACPI subsystem responds to lid close and keypress events.

The video driver is relevant for suspend/hibernate, very relevant.

---

### Post by jwbaker on 2010-04-26
Suspend, hibernate, and resume all work fine if I invoke them from the menu.  The problem is the machine doesn't do them automatically when I close the lid or use Fn+F4.

---

### Post by LKjell on 2010-04-26
You can either check gnome-power-preferences and see if the setting is correct there. Or you can tweak the gconf-editor to your needs. Third is to check that you are allowed to suspend in 
/usr/share/polkit-1/actions/org.freedesktop.upower.policy
Also check that your keyboard is not broken.

---

### Post by jwbaker on 2010-04-26
Keyboard works fine obviously, because everything works in previous Karmic when I reboot into it.  acpi_listen shows nothing when I type Fn+F4.

---

### Post by koso on 2010-04-27
I can confirm this. There is no problem with sleep script .. but problem is, that acpi is not receiving Fn+F4 events. When testing with acpi_listen , only sometimes is this event received, and action scritp is never run.

And btw. I am kubuntu user ...

---

