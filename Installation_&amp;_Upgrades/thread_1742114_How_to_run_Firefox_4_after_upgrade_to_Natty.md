---
title: "How to run Firefox 4 after upgrade to Natty"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by ratcheer on 2011-04-28
I just upgraded from Maverick to Natty. My main account still runs Firefox 3.6. However, I know that Firefox 4 is installed, because I created a new user and it runs Firefox 4.

How do I get my main user account to run Firefox 4 from Unity?

Thanks,
Tim

---

### Post by lovinglinux on 2011-04-28
All your accounts should be using Firefox 4, since is not the user profile that determines which version of Firefox to use.

Make sure you close Firefox, kill the *firefox-bin* process and start again. It should load the new Firefox version.

If you still experiencing problems, then please run the following commands and post the contents of the *firefox-report.txt* file generated in your desktop.

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
```

Please check the [Firefox 4 Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247") for further support on Firefox 4. Lots of info there.

---

### Post by ratcheer on 2011-04-28
Thank you. I am still having the problem, and here is the output of that script. A couple of things seem to be missing from /usr/local/bin, but as I said in the OP, Firefox 4 runs fine for a new user.

```
Ubuntu Architecture

Linux tim-mav-prod 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

Firefox Packages

firefox                                         install
firefox-branding                                install
firefox-globalmenu                              install
firefox-gnome-support                           install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-4.0/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: POSIX shell script text executable

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

ferramroberto-vlc-maverick.list
ferramroberto-vlc-maverick.list.distUpgrade
ferramroberto-vlc-maverick.list.save
libreoffice-ppa-maverick.list
libreoffice-ppa-maverick.list.save
tualatrix-ppa-maverick.list
tualatrix-ppa-maverick.list.distUpgrade
tualatrix-ppa-maverick.list.save
ubuntu-audio-dev-ppa-maverick.list
ubuntu-audio-dev-ppa-maverick.list.distUpgrade
ubuntu-tweak-stable.list.save

```

Tim

PS - All of those PPA sources were disabled by the Natty upgrade process, and they remain disabled.

---

### Post by lovinglinux on 2011-04-28
> **ratcheer said:**
> Thank you. I am still having the problem, and here is the output of that script. A couple of things seem to be missing from /usr/local/bin, but as I said in the OP, Firefox 4 runs fine for a new user.

```
Ubuntu Architecture

Linux tim-mav-prod 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

Firefox Packages

firefox                                         install
firefox-branding                                install
firefox-globalmenu                              install
firefox-gnome-support                           install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-4.0/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: POSIX shell script text executable

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

ferramroberto-vlc-maverick.list
ferramroberto-vlc-maverick.list.distUpgrade
ferramroberto-vlc-maverick.list.save
libreoffice-ppa-maverick.list
libreoffice-ppa-maverick.list.save
tualatrix-ppa-maverick.list
tualatrix-ppa-maverick.list.distUpgrade
tualatrix-ppa-maverick.list.save
ubuntu-audio-dev-ppa-maverick.list
ubuntu-audio-dev-ppa-maverick.list.distUpgrade
ubuntu-tweak-stable.list.save

```

Tim

PS - All of those PPA sources were disabled by the Natty upgrade process, and they remain disabled.

Looks like you have a Firefox manually installed in the opt folder. You could simply delete it, with the following command:

```
sudo rm -fr /opt/firefox
```

How are you launching your old Firefox profile? If you  have a custom launcher on your desktop, you need to edit it to point to the default Firefox. Let me know if this is the case, then I give you the instructions.

---

### Post by ratcheer on 2011-04-28
Thank you, again. Here is what happened. When I removed the old, manually installed copy of Firefox, Firefox would no longer start at all. So, I ran aptitude to remove Firefox, then I reinstalled it. Now, my primary user runs Firefox 4.

But, now I no longer have my Java plugin. I will work on reinstalling it, next.

Tim

---

### Post by ratcheer on 2011-04-29
Ok, I got the Java plugin reinstalled and it is working with Firefox.

However, there is still a small problem. I have to start FF by running /usr/lib/firefox-4.0/firefox.sh from a terminal. If I click the FF icon in the Unity bar, it flashes for a few seconds, then nothing happens.

How do I reconnect the Unity FF icon back to the script so it will start FF?

Tim

---

### Post by lovinglinux on 2011-04-29
> **ratcheer said:**
> Ok, I got the Java plugin reinstalled and it is working with Firefox.

However, there is still a small problem. I have to start FF by running /usr/lib/firefox-4.0/firefox.sh from a terminal. If I click the FF icon in the Unity bar, it flashes for a few seconds, then nothing happens.

How do I reconnect the Unity FF icon back to the script so it will start FF?

Tim

Unity is something totally new for me.

Try this: [http://ubuntuforums.org/showthread.php?t=1702422](http://ubuntuforums.org/showthread.php?t=1702422)

What happens if you type just *firefox* in a terminal?

---

### Post by ratcheer on 2011-04-29
Running the "firefox" command from a terminal also starts FF 4. However, it seemed in some way to be different, because it asked me again to set Firefox as the default web browser.

It still does not start by clicking the Unity FF icon. The icon flashes for a few seconds, then nothing happens.

With some trepidation, I will try to run the gsettings command from the thread you referenced.

Thank you,
Tim

---

### Post by ratcheer on 2011-04-29
No, running this code did not change the situation.

```
gsettings reset com.canonical.Unity.Launcher favorite-migration
```

Tim

---

### Post by ratcheer on 2011-04-29
Ok, I solved the problem. I may have cheated, but it is fixed.

I logged out of Unity and logged back in to Classic Gnome. When I clicked the Firefox icon there, it informed me that it could not find /opt/firefox. So, I right clicked the icon, selected Properties, and edited it to specify /usr/lib/firefox/firefox-4.0/firefox.sh

Then, I tried it from the menu entry, which had the same problem. I edited the properties of the menu entry the same way, then it worked, too.

I logged back off, logged back in to Unity, and now the icon works. It is a real pain that Unity gives you no simple way to find and edit the properties of an icon. :mad:  I may just go back to Gnome Classic, or I may try to figure out how to migrate my production instance to my testing instance, which is running Gnome3 and gnome-shell.

Thanks for all your help, lovinglinux.

Tim

---

### Post by lovinglinux on 2011-04-29
> **ratcheer said:**
> Ok, I solved the problem. I may have cheated, but it is fixed.

I logged out of Unity and logged back in to Classic Gnome. When I clicked the Firefox icon there, it informed me that it could not find /opt/firefox. So, I right clicked the icon, selected Properties, and edited it to specify /usr/lib/firefox/firefox-4.0/firefox.sh

Then, I tried it from the menu entry, which had the same problem. I edited the properties of the menu entry the same way, then it worked, too.

I logged back off, logged back in to Unity, and now the icon works. It is a real pain that Unity gives you no simple way to find and edit the properties of an icon. :mad:  I may just go back to Gnome Classic, or I may try to figure out how to migrate my production instance to my testing instance, which is running Gnome3 and gnome-shell.

Thanks for all your help, lovinglinux.

Tim

You are welcome.

You could also log into Gnome Classic and check if /usr/bin/firefox is the default browser. I am not sure what is happening, because Unity is completely new too me. Perhaps you have a custom /usr/bin/firefox pointing to the wrong direction.

The workaround works anyway.

This problem with Unity not being able to easily edit the launchers will generate a lot of complaints.

---

