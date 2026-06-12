---
title: "Issue with 16.04 package files + /etc/apt/sources.list seems to have disappeared?!"
date: 2019-03-24
forum: Installation &amp; Upgrades
---

### Post by SiddharthaWolf on 2019-03-24
Hello,

Over the past few months, I've been getting the red warning icon on my indicator bar telling me that something is wrong with the packages, but after I do **sudo rm /etc/apt/sources.list** and the usual update stuff, it tends to return to normal. However, I do all this stuff around my pretty busy work schedule so am mainly just trying to keep things superficially tidy and keeping the warning messages at bay without ever getting to the root, so to speak.

However, recently it's gotten pretty bad so I thought I'd attempt an upgrade to 18.04. Couldn't do that because I was told that there was a package that required an update (iirc) and it remained so after sudo apt-get update etc. Weird. Anyway, I learnt that it was lutris and I just removed it because I really wanted to get this sorted. So some morning last week I got it all started prepping for 18.04.

Then at about 7pm the same day I was about to pack it up when I noticed behind the dozens of tabs and programs I had started the 18.04 upgrade. I didn't have time to go through with it, so to the "Do you want to proceed with the upgrade?" prompt, I chose N.

I thought that would all be OK, but now it seems something is majorly afoot with my packages. 

Specifically, the **/etc/apt/sources.list** seemed to have disappeared when I tried to do **sudo rm /etc/apt/sources.list**, as I got the message saying that that directory did not exist. I have since pasted in a proper 16.04 packages list, though I wasn't sure if this was really a good idea. It seems to have worked, since I get no error message here though.

I went back to do **sudo apt-get update **and all appeared to be fine except the end of the process returned a series of warnings followed by this:

```
*E: Unable to parse package file /var/lib/apt/lists/ppa.launchpad.net_knapsu_openxcom_ubuntu_dists_xenial_main_binary-amd64_Packages (1)*
*E: Unable to parse package file /var/lib/apt/lists/ppa.launchpad.net_knapsu_openxcom_ubuntu_dists_xenial_main_binary-i386_Packages (1)*
*E: Unable to parse package file /var/lib/apt/lists/ppa.launchpad.net_knapsu_openxcom_ubuntu_dists_xenial_main_binary-all_Packages (1)*
*E: Unable to parse package file /var/lib/apt/lists/ppa.launchpad.net_knapsu_openxcom_ubuntu_dists_xenial_main_i18n_Translation-en%5fGB (1)*
*E: Unable to parse package file /var/lib/apt/lists/ppa.launchpad.net_knapsu_openxcom_ubuntu_dists_xenial_main_i18n_Translation-en (1)*
*W: You may want to run apt-get update to correct these problems*
*E: The package cache file is corrupted*
```

Out of interest/desperation I also thought I'd try **sudo do-release-upgrade **but was informed that I should [I]Please install all available updates for your release before upgrading.

[/I]When I tried to check the update settings using the GUI, I saw that all Ubuntu Options had been unchecked, and there were numerous seeming duplicated in my Other Software list. I, probably foolishly, checked all the Ubuntu Options boxes and then tried to apply the changes, when I got the message:

```
*Failed to load the package list*

*This is a serious problem. Try again later. If this problem appears again, please report an error to the developers.* 
```

With the details:

```
*W:Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/arx-ubuntu-release-xenial.list:2 and /etc/apt/sources.list.d/arx-ubuntu-release-xenial.list:3, W:Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/arx-ubuntu-release-xenial.list:2 and /etc/apt/sources.list.d/arx-ubuntu-release-xenial.list:4, W:Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/arx-ubuntu-release-xenial.list:2 and /etc/apt/sources.list.d/arx-ubuntu-release-xenial.list:5, E:Unable to parse package file /var/lib/apt/lists/ppa.launchpad.net_knapsu_openxcom_ubuntu_dists_xenial_main_binary-amd64_Packages (1), E:Unable to parse package file /var/lib/apt/lists/ppa.launchpad.net_knapsu_openxcom_ubuntu_dists_xenial_main_binary-i386_Packages (1), E:Unable to parse package file /var/lib/apt/lists/ppa.launchpad.net_knapsu_openxcom_ubuntu_dists_xenial_main_binary-all_Packages (1), E:Unable to parse package file /var/lib/apt/lists/ppa.launchpad.net_knapsu_openxcom_ubuntu_dists_xenial_main_i18n_Translation-en (1), E:Unable to parse package file /var/lib/apt/lists/ppa.launchpad.net_knapsu_openxcom_ubuntu_dists_xenial_main_i18n_Translation-en%%5fGB (1), W:You may want to run apt-get update to correct these problems, E:The package cache file is corrupted*

```
It seems kinda self-explanatory, but I've tried to fix this intuitively for a while now and don't seem to be getting anywhere with it, so am hoping that you might be able to help.

I'm not sure if it's relevant, but also when I tried to use (gksudo) nautilus via the terminal I was allowed, but got this message too:

```
*(nautilus:22598): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed*
```



When I tried (vanilla) nautilus again I got this:
```

*(nautilus:22188): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed*

*(nautilus:22188): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed*

*(nautilus:22188): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed*

*(nautilus:22188): GLib-GObject-WARNING **: invalid (NULL) pointer instance*

*(nautilus:22188): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed*
```



What's the simplest way to remedy this mess? Is there any way I can do so without having to reinstall Ubuntu?

Thanks!

---

### Post by mörgæs on 2019-03-26
I would recommend a fresh install. 

If any problems appear then don't delete sources.list. Better to ask for help here.

---

### Post by ajgreeny on 2019-03-26
You could try renaming whatever currently is your /etc/apt/sources.list file and then rebuild a new file using this site that I have had to use once a long time ago.
[https://repogen.simplylinux.ch/](https://repogen.simplylinux.ch/)

You can just choose country, ubuntu version, etc etc, even add a few ppa repos if you need them, then save the file it generates to /etc/apt/sources.list

Your current file appears a bit unusual with ppa repos I do not recognise so I wonder if that **launchpad.net_knapsu_openxcom** site no longer exists, at least for xenial?

---

### Post by deadflowr on 2019-03-26
> I wonder if that launchpad.net_knapsu_openxcom site no longer exists, 
It exists :
[https://launchpad.net/~knapsu/+archive/ubuntu/openxcom]("https://launchpad.net/~knapsu/+archive/ubuntu/openxcom")
And still supported.

You can grab a base sources.list file from
/usr/share/doc/apt/examples.
And then just copy it into the /etc/apt directory.
But it only has the main and restricted repos enabled.
But can easily add-apt-repository universe and multiverse.

Somehow it looks like the OP really wanted to clear the /var/lib/apt/lists directory.

---

### Post by SiddharthaWolf on 2019-03-27
Hello kind Ubuntu folk,

Yeah, I have no idea what happened tbh, but since I work on my laptop I thought it best just to do a clean install on Sunday evening. Thankfully, I was able to keep the old Ubuntu - thought it was only functioning in TTY for some reason - on a separate partition, so I could access files I hadn't backed up etc.

My problem now is that I swore when I was doing the installation that it said that my old partition would be 28GB and my new one 220GB, which seemed fine. However, probably because I was doing this at 00:30 and couldn't think straight, it turns out it was the other way around. So I now have an active 28GB Ubuntu 18.04 partition (really liking 18.04 btw, despite taking a while to adapt to Gnome over Unity) with 220GB that I have to mount. Is there any way I can resize the partitions safely? Presumably through GParted using the live USB? It makes sense in my head, but are there any potential problems I might not have seen? I am apparently using 168GB of that partition, god knows how (though I imagine a mass of PDFs and audio files would be deceptively large), but I'll have to trim that down first obviously. 

Can I do all that safely? Or perhaps it'd just be best for me to get all the vital stuff onto a USB and wipe the old partition completely, considering it's pretty much broken?

---

### Post by mörgæs on 2019-03-27
If you have the storage at hand then I suggest that you copy the individual files from your old partition (not the entire /home which is probably full of cruft) onto a USB drive. After that a fresh install. 

You could also resize using Gparted in a live boot. I have never experienced problems but it's a single point of failure so a backup is good to have - which leads to the option mentioned above.

---

