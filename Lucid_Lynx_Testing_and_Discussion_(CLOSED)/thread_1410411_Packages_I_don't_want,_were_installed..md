---
title: "Packages I don't want, were installed."
date: 2010-02-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by cariboo on 2010-02-18
Does anyone have any idea why alien, rpm and postfix were installed with the current updates? I don't use any of them. I also noticed they were installed on the current Karmic update.

---

### Post by howefield on 2010-02-18
Chrome pulled them in.

---

### Post by VMC on 2010-02-18
> **cariboo907 said:**
> Does anyone have any idea why alien, rpm and postfix were installed with the current updates? I don't use any of them. I also noticed they were installed on the current Karmic update.
I wondered why also. Then I saw Chrome also in the mix. I haven't seen a Chrome update in ages, if at all. Why rpm and the rest of ref hat stuff?

---

### Post by howefield on 2010-02-18
> **VMC said:**
> I wondered why also. Then I saw Chrome also in the mix. I haven't seen a Chrome update in ages, if at all. Why rpm and the rest of ref hat stuff?

Chrome is updating from version 5.307.7 to 5.307.9, but wants to install some really strange dependancies which as I understand it, will be fixed in the next update.

---

### Post by Ibidem on 2010-02-18
Check for lsb or xarchiver, maybe?

---

### Post by mendieta on 2010-02-18
> **howefield said:**
> Chrome is updating from version 5.307.7 to 5.307.9, but wants to install some really strange dependancies which as I understand it, will be fixed in the next update.

Oh, do you know that for a fact? Do you have a link to a proper source of info? I think I'll wait for next update.

It seems to me like they pulled the LSB in, which means they need to support RPM, and thus alien, too. See also here:
[http://www.google.com/support/forum/p/Chrome/thread?tid=04fc1d93c7ec8185&hl=en&fid=04fc1d93c7ec818500047fe9bcf5550d](http://www.google.com/support/forum/p/Chrome/thread?tid=04fc1d93c7ec8185&hl=en&fid=04fc1d93c7ec818500047fe9bcf5550d)

Thanks!

---

### Post by emarkay on 2010-02-18
Yea, every time I reinstall, I have to Synaptic out the following...

*Bluetooth/Bluez, Brasero, Britty, F-Spot, Gnome Games, Modemmanager, Plymouth, Rhythmbox, Tomboy, Totem, Unneeded Fonts, Vinagre, Virtuoso.*

Wouldn't in be nice to be able to have a "template" that allows a "pre-install configuration to automagically prepare the installation, and even add the following I want everytime:
[I]
Alsa*, Aucacity, Avidemux, Backports-Modules, Byzanz, BleachBit, BOINC, Checksecurity, Chkrootkit, Conky, Create-Resources, Gedit*, Gimp*, Gnome-Format, HPLIP*,K3b*, Kompozer, Libk3b(x)*, Localepurge, Ntfs-Config, Samba*, Sane*, Smbfs, Sun-Java 6, Sysinfo, System-Config-Samba, Thunar, Thunderbird*, Ubuntu Restricted Extras, VLC, WINE 1.2, XVidCap.[/I]



Maybe for the next release...



[FONT=Times New Roman, serif][SIZE=3]
[/SIZE][/FONT]

---

### Post by Bachstelze on 2010-02-18
> **emarkay said:**
> Yea, every time I reinstall, I have to Synaptic out the following...


The point. You missed it.

---

### Post by emarkay on 2010-02-18
> **Bachstelze said:**
> The point. You missed it.

I was just agreeing and offering sympathy - and maybe another "peep" for a "brainstorm"...

---

### Post by VMC on 2010-02-18
> **Bachstelze said:**
> The point. You missed it.

Thank you! I studied his reply trying to make sense of it, then gave up and came to your reply. LOL.

---

### Post by jeremy1138 on 2010-02-18
> **Bachstelze said:**
> The point. You missed it.

LOL Yeah that one confused me too.:D

---

### Post by IanW on 2010-02-19
> **emarkay said:**
> Yea, every time I reinstall, I have to Synaptic out the following...

*Bluetooth/Bluez, Brasero, Britty, F-Spot, Gnome Games, Modemmanager, Plymouth, Rhythmbox, Tomboy, Totem, Unneeded Fonts, Vinagre, Virtuoso.*

Wouldn't in be nice to be able to have a "template" that allows a "pre-install configuration to automagically prepare the installation, and even add the following I want everytime:
[I]
Alsa*, Aucacity, Avidemux, Backports-Modules, Byzanz, BleachBit, BOINC, Checksecurity, Chkrootkit, Conky, Create-Resources, Gedit*, Gimp*, Gnome-Format, HPLIP*,K3b*, Kompozer, Libk3b(x)*, Localepurge, Ntfs-Config, Samba*, Sane*, Smbfs, Sun-Java 6, Sysinfo, System-Config-Samba, Thunar, Thunderbird*, Ubuntu Restricted Extras, VLC, WINE 1.2, XVidCap.[/I]



Maybe for the next release...



[FONT=Times New Roman, serif][SIZE=3]
[/SIZE][/FONT]


You could select your usual changes in Synaptic and "Save Markings" to a USB stick before applying it.
Then re-load it once you've re-installed.

I agree that it would be nice to be able to point the installer to such a list during the install process.

---

### Post by Jordanwb on 2010-02-19
> **emarkay said:**
> Wouldn't in be nice to be able to have a "template" that allows a "pre-install configuration to automagically prepare the installation, and even add the following I want everytime:

Automagically? I just wrote a script and run that. It uninstalls the packages I don't need, adds repos I want and installs packages I do want.

---

### Post by VMC on 2010-02-19
> **IanW said:**
> ...I agree that it would be nice to be able to point the installer to such a list during the install process.Doesn't alternate advance do that for you?

---

### Post by ronacc on 2010-02-19
> **emarkay said:**
> Yea, every time I reinstall, I have to Synaptic out the following...

*Bluetooth/Bluez, Brasero, Britty, F-Spot, Gnome Games, Modemmanager, Plymouth, Rhythmbox, Tomboy, Totem, Unneeded Fonts, Vinagre, Virtuoso.*

Wouldn't in be nice to be able to have a "template" that allows a "pre-install configuration to automagically prepare the installation, and even add the following I want everytime:
[I]
Alsa*, Aucacity, Avidemux, Backports-Modules, Byzanz, BleachBit, BOINC, Checksecurity, Chkrootkit, Conky, Create-Resources, Gedit*, Gimp*, Gnome-Format, HPLIP*,K3b*, Kompozer, Libk3b(x)*, Localepurge, Ntfs-Config, Samba*, Sane*, Smbfs, Sun-Java 6, Sysinfo, System-Config-Samba, Thunar, Thunderbird*, Ubuntu Restricted Extras, VLC, WINE 1.2, XVidCap.[/I]



Maybe for the next release...



[FONT=Times New Roman, serif][SIZE=3]
[/SIZE][/FONT]

a template or choice of apps at install has been discussed before , basically Ubuntu is determined to keep the install as simple as possible with as few questions (options) as possible during the install, since  the choice of apps can be modified afterwards .

---

### Post by howefield on 2010-02-19
> **mendieta said:**
> Oh, do you know that for a fact?

No, I said "as I understand it". Were I speaking facts, I'd have said so.

[http://code.google.com/p/chromium/issues/detail?id=35639](http://code.google.com/p/chromium/issues/detail?id=35639)

---

### Post by Ibidem on 2010-02-19
Something like Fedora's kickstart would be nice, maybe.
Fedora-Kickstart
Slax/Nimblex-build custom CD on their server.
SUSE-SUSE Studio
Ubuntu- mainly UCK.

Does anyone else see the difference?

---

### Post by Mr. Picklesworth on 2010-02-19
Oops, I linked to the bug report but Howefield beat me to it by 6 hours :)

---

### Post by mendieta on 2010-02-19
> **howefield said:**
> No, I said "as I understand it". Were I speaking facts, I'd have said so.

[http://code.google.com/p/chromium/issues/detail?id=35639](http://code.google.com/p/chromium/issues/detail?id=35639)

Yes, I found that bug report earlier today, I came here to post a link to it but I see you did. In short, and for anyone who didn't update their chrome, **Google will be fixing this, so it's worthwhile to wait for a later update**.

Thanks, and perhaps we can chill a little, pedantic posts like yours make me come here a lot less often than I could, which is probably a shame since Free Software is all about brotherhood/sisterhood/cooperation.

---

### Post by castrojo on 2010-02-19
> **Ibidem said:**
> Something like Fedora's kickstart would be nice, maybe.

? I've been kickstarting Ubuntu installs for years. It's totally supported.

---

### Post by howefield on 2010-02-19
> **mendieta said:**
> Thanks, and perhaps we can chill a little, pedantic posts like yours make me come here a lot less often than I could, which is probably a shame since Free Software is all about brotherhood/sisterhood/cooperation.

Good idea, hot under the collar posts like yours don't help.

---

