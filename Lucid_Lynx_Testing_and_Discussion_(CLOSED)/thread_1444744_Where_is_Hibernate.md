---
title: "Where is Hibernate ?"
date: 2010-04-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by timosha on 2010-04-01
Since the last updates I don't have Hibernate anymore ! Not in the applet and not when I enter CTRL-ALT-DEL.

---

### Post by arnab_das on 2010-04-01
not really a solution to ur problem, but if u need to hibernate urgently, then u should take a look at this: [http://ubuntuforums.org/showthread.php?t=329902](http://ubuntuforums.org/showthread.php?t=329902)

---

### Post by LKjell on 2010-04-01
Do you get the option when you type this in a terrminal?
```
gnome-session-save --gui --shutdown-dialog
```

---

### Post by timosha on 2010-04-02
> **LKjell said:**
> Do you get the option when you type this in a terrminal?
```
gnome-session-save --gui --shutdown-dialog
```

No, I don't get the option.

And in Power Management -> On Battery Power -> When battery power is critically low : I can not select hibernate anymore (only suspend and shutdown).

---

### Post by LKjell on 2010-04-02
Then hibernate is disabled for you or your video driver does not support it. You might try to enable it through policykit. The file to edit is 
[B]
/usr/share/polkit-1/actions/org.freedesktop.upower.policy[/B]

Then edit line 36 to **<allow_active>yes</allow_active>**.
If it already says yes then file a bug report against the upower package.

---

### Post by timosha on 2010-04-02
The problem is solved. For one reason or the other the UUID of my swap partition was changed. Replaced the old UUID in fstab with the new one and everything is working again.

Why would the UUID of a partition suddenly change ?

---

