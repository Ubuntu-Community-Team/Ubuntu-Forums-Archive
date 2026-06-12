---
title: "Gnome terminal bugs"
date: 2010-01-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by phenest on 2010-01-28
I've reported a couple of bugs to Gnome. Can anyone that uses Bugzilla please confirm these bugs.

[bug 608361]("https://bugzilla.gnome.org/show_bug.cgi?id=608361")
[bug 608360]("https://bugzilla.gnome.org/show_bug.cgi?id=608360")

---

### Post by ranch hand on 2010-01-28
> **phenest said:**
> I've reported a couple of bugs to Gnome. Can anyone that uses Bugzilla please confirm these bugs.

[bug 608361]("https://bugzilla.gnome.org/show_bug.cgi?id=608361")
[bug 608360]("https://bugzilla.gnome.org/show_bug.cgi?id=608360")
On the first bug they have a comment to report this to launchpad;
> 
Please complain about this downstream on launchpad; this is from a ubuntu-only[FONT=monospace] [/FONT]patch.

Second bug does not effect me possibly because I have localepurge installed.

They have this comment;
> [FONT=monospace]
[/FONT]That's simply because the en-gb translation hasn't translated some strings yet.


---

### Post by Gourgi on 2010-01-28
> **ranch hand said:**
> On the first bug they have a comment to report this to launchpad;
> 
Please complain about this downstream on launchpad; this is from a ubuntu-onlypatch. 


and this is the exact reason why we should firstly file bugs in launchpad and then upstream (if they need to).
I had to learn it the same way as you did phenest, after filing a bug i had in gnome-bugzilla.

---

### Post by Simian Man on 2010-01-28
> **Gourgi said:**
> and this is the exact reason why we should firstly file bugs in launchpad and then upstream (if they need to).
I had to learn it the same way as you did phenest, after filing a bug i had in gnome-bugzilla.

In most other distros you don't have to do this.  Ubuntu just patches the crap out of everything.

---

### Post by phenest on 2010-01-28
> **Gourgi said:**
> and this is the exact reason why we should firstly file bugs in launchpad and then upstream (if they need to).
I had to learn it the same way as you did phenest, after filing a bug i had in gnome-bugzilla.

Because you can't file bugs on LP for gnome terminal.

---

### Post by autark on 2010-01-28
> **Gourgi said:**
> and this is the exact reason why we should firstly file bugs in launchpad and then upstream (if they need to).
I had to learn it the same way as you did phenest, after filing a bug i had in gnome-bugzilla.

I've had the reverse experience, reporting bugs in Launchpad and having people saying I should have reported them upstream. So I started reporting bugs upstream first, only to discover that some things were indeed Ubuntu-specific. :-(

---

### Post by phenest on 2010-01-28
> **autark said:**
> I've had the reverse experience, reporting bugs in Launchpad and having people saying I should have reported them upstream. So I started reporting bugs upstream first, only to discover that some things were indeed Ubuntu-specific. :-(

Even to the point where you tossed from one to the other, almost as if neither wants to take responsibility.

So, in this case case, which is it? Gnome devs as usual just shrug it off.

---

### Post by Gourgi on 2010-01-29
> **phenest said:**
> Because you can't file bugs on LP for gnome terminal.
i don't understand that.
***ubuntu-bug gnome-terminal*** works for me and you can file bugs here [https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+filebug](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+filebug)


[QUOTE=autark]I've had the reverse experience, reporting bugs in Launchpad and having people saying I should have reported them upstream. So I started reporting bugs upstream first, only to discover that some things were indeed Ubuntu-specific. :-( [/QUOTE]
i know that, it is the common behaviour.

At least from my bug  reports , i file them firstly in launchpad and after they are triaged or not being replied for a long time, i forward them upstream and then get back to launchpad and file the upstream bug url. That way you can monitor if a bug is fixed either upstream or in launchpad/ubuntu only.
my direct upstream reports are the feaure requests.

---

### Post by phenest on 2010-01-29
> **Gourgi said:**
> i don't understand that.
***ubuntu-bug gnome-terminal*** works for me and you can file bugs here [https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+filebug](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+filebug)

I figured to look for the package on LP first before using ubuntu-bug, but if you search for 'gnome terminal' in LP, you get this page: [https://bugs.launchpad.net/gnome-terminal]("https://bugs.launchpad.net/gnome-terminal"). But then I realised, you search for 'ubuntu' and then for the gnome terminal package (if you know the package name).

Oh well.

---

### Post by MaX on 2010-01-30
> **phenest said:**
> I figured to look for the package on LP first before using ubuntu-bug, but if you search for 'gnome terminal' in LP, you get this page: [https://bugs.launchpad.net/gnome-terminal]("https://bugs.launchpad.net/gnome-terminal"). But then I realised, you search for 'ubuntu' and then for the gnome terminal package (if you know the package name).

Oh well.

Yes Launchpad could point you to the correct location you'd think...

---

### Post by MacUntu on 2010-01-30
```
--- old/debian/patches/20_add_alt_screen_toggle_ui.patch	2010-01-30 14:34:16.423647297 +0100
+++ new/debian/patches/20_add_alt_screen_toggle_ui.patch	2010-01-30 14:34:55.443646169 +0100
@@ -69,8 +69,8 @@
 + 		<packing>
 + 		  <property name="left_attach">0</property>
 + 		  <property name="right_attach">2</property>
-+ 		  <property name="top_attach">4</property>
-+ 		  <property name="bottom_attach">5</property>
++ 		  <property name="top_attach">5</property>
++ 		  <property name="bottom_attach">6</property>
 + 		  <property name="y_options"></property>
 + 		</packing>
 + 	      </child>
```

gives me:

[IMG]http://img.xrmb2.net/images/572711.png[/IMG]

Not sure if that's all you need to do, though.

---

