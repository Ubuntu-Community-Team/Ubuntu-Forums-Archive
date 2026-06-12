---
title: "Askin for password on every trifle"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by TheLions on 2009-10-24
I installed fresh Karmic a day ago, and I'm very pleased with it, but it asks me for root password on every trifle. 
I want change CPU mode on CPU Frequency Scaling Monitor from "Ondemand" to "Performance", no can't do, enter pass first. 
Then I want to listen some music from one of my NTFS partitions, no can't do, enter pass first to mount it. Frack, wrong partition, it is on other one NTFS, enter pass.
Also it asks me password when shutting down with root logged in and when waking up from suspend and hibrnate.

So if someone could help me to disable password requests when:

1)changing cpu freq in CPU Frequency applet in Gnome panel
2)mounting NTFS
3)shutting down with another user logged in
4)waking up from suspend/hiberante

---

### Post by TrueTom on 2009-10-24
Ubuntu is the new Vista... :)

---

### Post by mc4man on 2009-10-24
Coming to karmic from hardy it was a little odd to see a couple of new terms such as authentication agent and untrusted application launcher

As far as the mounting of internal drives and cpu applet it seems you're given 5 mins before needing to authenticate again.

While the only file i found that set timeouts at 300 secs had no effect if edited, for the moment have eliminated the need to authenticate the mounting internal drives at all. (first/admin user)

**as to the advisability of doing so I don't know,** seems to be working fine, setting has remained thru a reboot.

You can find files of interest in these matters in 
/usr/share/polkit-1/actions/

For internal drives changed the orig
 > <action id="org.freedesktop.devicekit.disks.filesystem-mount-system-internal">
    <description>Mount a system-internal device</description>
    <description xml:lang="da">Montér en intern enhed</description>
    <description xml:lang="de">Eingebautes Gerät einhängen</description>
    <message>Authentication is required to mount the device</message>
    <message xml:lang="da">Autorisering er påkrævet for at montere et fil system</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um das Gerät einzuhängen</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>[COLOR="Blue"]auth_admin_keep[/COLOR]</allow_active>
    </defaults>
  </action>

to this 
> <action id="org.freedesktop.devicekit.disks.filesystem-mount-system-internal">
    <description>Mount a system-internal device</description>
    <description xml:lang="da">Montér en intern enhed</description>
    <description xml:lang="de">Eingebautes Gerät einhängen</description>
    <message>Authentication is required to mount the device</message>
    <message xml:lang="da">Autorisering er påkrævet for at montere et fil system</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um das Gerät einzuhängen</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>[COLOR="Blue"]yes[/COLOR]</allow_active>
    </defaults>
  </action>


The other change, "untrusted application launcher", doesn't seem to have any negative effect atm other than not allowing an icon to be set until it is marked as trusted. ( does seem a little vista-ish

edit 
see edit below, ( formatting and devicekit updates

---

### Post by flipper9 on 2009-10-24
Yeah; it really is annoying having to "ask permisson" just to change something simple as the frequency scaling of the processor.  Is there a GUI tool where we can say what things will and will not require authorization?  And the 5 minute timeout is kinda usless since I don't change the frequency every 2 minutes.

---

### Post by mc4man on 2009-10-24
Moving over to my laptop and again following same idea as previous post.
( also again note I'm not commenting on the advisability or whether this will survive or be needed with an update to devicekit* or whatever

```
gksudo gedit /usr/share/polkit-1/actions/org.gnome.cpufreqselector.policy

```

**carefully** edit as such (scroll down to bottom, showing group for reference

orig.
> <message xml:lang="vi">C&#7847;n quy&#7873;n &#273;&#7863;c bi&#7879;t &#273;&#7875; thay &#273;&#7893;i t&#7927; l&#7879; t&#7847;n s&#7889; CPU.</message>
    <message xml:lang="zh_CN">&#35201;&#26356;&#25913; CPU &#39057;&#29575;&#33539;&#22260;&#65292;&#38656;&#35201;&#19968;&#23450;&#29305;&#26435;&#12290;</message>
    <message xml:lang="zh_HK">&#35201;&#35519;&#25972; CPU &#38971;&#29575;&#38656;&#35201;&#27402;&#38480;&#12290;</message>
    <message xml:lang="zh_TW">&#35201;&#35519;&#25972; CPU &#38971;&#29575;&#38656;&#35201;&#27402;&#38480;&#12290;</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>[COLOR="Blue"]auth_admin_keep[/COLOR]</allow_active>
    </defaults>
  </action>

</policyconfig>

edited
> <message xml:lang="vi">C&#7847;n quy&#7873;n &#273;&#7863;c bi&#7879;t &#273;&#7875; thay &#273;&#7893;i t&#7927; l&#7879; t&#7847;n s&#7889; CPU.</message>
    <message xml:lang="zh_CN">&#35201;&#26356;&#25913; CPU &#39057;&#29575;&#33539;&#22260;&#65292;&#38656;&#35201;&#19968;&#23450;&#29305;&#26435;&#12290;</message>
    <message xml:lang="zh_HK">&#35201;&#35519;&#25972; CPU &#38971;&#29575;&#38656;&#35201;&#27402;&#38480;&#12290;</message>
    <message xml:lang="zh_TW">&#35201;&#35519;&#25972; CPU &#38971;&#29575;&#38656;&#35201;&#27402;&#38480;&#12290;</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>[COLOR="Blue"]yes[/COLOR]</allow_active>
    </defaults>
  </action>

</policyconfig>

Edit
note that these quote boxes are not showing the formatting, **Do Not change** the existing format, just replace blue

re-edit
kept back a devicekit update today till after setting no auth.. on internal drives and cpu applet.
The update returned the setting back to "auth_admin_keep", went in and changed back to "yes" again.

So an update may cause auth... to return, only takes a sec or to to reset back to no auth...

---

### Post by TheLions on 2009-10-24
> **mc4man said:**
> Coming to karmic from hardy it was a little odd to see a couple of new terms such as authentication agent and untrusted application launcher

As far as the mounting of internal drives and cpu applet it seems you're given 5 mins before needing to authenticate again.

While the only file i found that set timeouts at 300 secs had no effect if edited, for the moment have eliminated the need to authenticate the mounting internal drives at all. (first/admin user)

**as to the advisability of doing so I don't know,** seems to be working fine, setting has remained thru a reboot.

You can find files of interest in these matters in 
/usr/share/polkit-1/actions/

For internal drives changed the orig
 

to this 


The other change, "untrusted application launcher", doesn't seem to have any negative effect atm other than not allowing an icon to be set until it is marked as trusted. ( does seem a little vista-ish

edit 
see edit below,

> **mc4man said:**
> Moving over to my laptop and again following same idea as previous post.
( also again note I'm not commenting on the advisability or whether this will survive or be needed with an update to devicekit* or whatever

```
gksudo gedit /usr/share/polkit-1/actions/org.gnome.cpufreqselector.policy

```

**carefully** edit as such (scroll down to bottom, showing group for reference

orig.


edited


Edit
note that these quote boxes are not showing the formatting, **Do Not change** the existing format, just replace blue

Thanks this solved 1) and 2) :)

i found solution for 4) : [http://ubuntuforums.org/showpost.php?p=2061391&postcount=4](http://ubuntuforums.org/showpost.php?p=2061391&postcount=4)
applications>accesories>terminal

type gconf-editor

go to the key at /apps/gnome-power-manager

look for lock_on_hibernate, disable it...theres one for suspend as well...

remains only 3)

---

### Post by mc4man on 2009-10-24
Note the "re-edit" about devicekit updates, no big deal to redo, maybe one of these updates will 'resolve' the issue from the ubuntu side (vs. user side

---

### Post by mc4man on 2009-10-24
#3 should be in 
/usr/share/polkit-1/actions/org.freedesktop.consolekit.policy
( both for stop and restart

---

### Post by TheLions on 2009-10-24
> **mc4man said:**
> #3 should be in 
/usr/share/polkit-1/actions/org.freedesktop.consolekit.policy
( both for stop and restart

Thank you so much!!! 

[[IMG]http://slike.hr/slike/m/mysmilie2901_42792.gif[/IMG]](http://slike.hr/)[[IMG]http://slike.hr/slike/m/mysmilie2901_42792.gif[/IMG]](http://slike.hr/)[[IMG]http://slike.hr/slike/m/mysmilie2901_42792.gif[/IMG]](http://slike.hr/)

---

