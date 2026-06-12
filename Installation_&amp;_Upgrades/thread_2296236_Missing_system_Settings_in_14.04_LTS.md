---
title: "Missing system Settings in 14.04 LTS"
date: 2015-09-24
forum: Installation &amp; Upgrades
---

### Post by exsheeple on 2015-09-24
Hello.  I have check and tried install the system settings from Synaptic, from software center, and via the terminal and Im still getting errors.  This is a fresh install on a dual booted system.  Here are the errors I received with Synaptic: 

```
E: libgl1-mesa-glx: 17.7449:subprocess installed post-installation script returned error exit status 2
E: libcogl15: 17.7449:dependency problems - leaving unconfigured
E: libcogl-pango15: 17.7449:dependency problems - leaving unconfigured
E: libclutter-1.0-0: 17.7449:dependency problems - leaving unconfigured
E: libclutter-gst-2.0-0: 17.7449:dependency problems - leaving unconfigured
E: gstreamer1.0-clutter: dependency problems - leaving unconfigured
E: libcheese7: 17.7449:dependency problems - leaving unconfigured
E: libclutter-gtk-1.0-0: 17.7449:dependency problems - leaving unconfigured
E: libcheese-gtk23: 17.7449:dependency problems - leaving unconfigured
E: libglamor0: 17.9298:dependency problems - leaving unconfigured
E: libwebkitgtk-3.0-0: 17.9298:dependency problems - leaving unconfigured
E: libgoa-backend-1.0-1: 17.9298:dependency problems - leaving unconfigured
E: libqt4-opengl: 17.9298:dependency problems - leaving unconfigured
E: libqt5gui5: 17.9298:dependency problems - leaving unconfigured
E: libqt5multimedia5: 17.9298:dependency problems - leaving unconfigured
E: libqt5feedback5: 17.9298:dependency problems - leaving unconfigured
E: libqt5widgets5: 17.9298:dependency problems - leaving unconfigured
E: libqt5opengl5: 17.9298:dependency problems - leaving unconfigured
E: libqt5printsupport5: 17.9298:dependency problems - leaving unconfigured
E: libqt5quick5: 17.9298:dependency problems - leaving unconfigured
E: libqt5svg5: 17.9298:dependency problems - leaving unconfigured
E: libqt5webkit5: 17.9298:dependency problems - leaving unconfigured
E: libqt5webkit5-qmlwebkitplugin: 17.9298:dependency problems - leaving unconfigured
E: libqtwebkit4: 17.9298:dependency problems - leaving unconfigured
E: qtdeclarative5-qtquick2-plugin: 17.9298:dependency problems - leaving unconfigured
E: libu1db-qt5-3: 17.9298:dependency problems - leaving unconfigured
E: qtdeclarative5-privatewidgets-plugin: 17.9298:dependency problems - leaving unconfigured
E: qtdeclarative5-dialogs-plugin: 17.9298:dependency problems - leaving unconfigured
E: qtdeclarative5-qtfeedback-plugin: 17.9298:dependency problems - leaving unconfigured
E: qtdeclarative5-u1db1.0: 17.9298:dependency problems - leaving unconfigured
E: qtdeclarative5-window-plugin: 17.9298:dependency problems - leaving unconfigured
E: qtdeclarative5-ubuntu-ui-toolkit-plugin: 17.9298:dependency problems - leaving unconfigured
E: qtdeclarative5-ubuntu-settings-components: 17.9298:dependency problems - leaving unconfigured
E: libglu1-mesa: 17.9298:dependency problems - leaving unconfigured
E: empathy: dependency problems - leaving unconfigured
E: mcp-account-manager-uoa: dependency problems - leaving unconfigured
E: account-plugin-aim: dependency problems - leaving unconfigured
E: signon-ui: dependency problems - leaving unconfigured
E: signon-plugin-oauth2: dependency problems - leaving unconfigured
E: libaccount-plugin-generic-oauth: dependency problems - leaving unconfigured
E: account-plugin-facebook: dependency problems - leaving unconfigured
E: account-plugin-flickr: dependency problems - leaving unconfigured
E: libaccount-plugin-google: dependency problems - leaving unconfigured
E: account-plugin-google: dependency problems - leaving unconfigured
E: account-plugin-identica: dependency problems - leaving unconfigured
E: account-plugin-jabber: dependency problems - leaving unconfigured
E: account-plugin-salut: dependency problems - leaving unconfigured
E: account-plugin-twitter: dependency problems - leaving unconfigured
E: account-plugin-yahoo: dependency problems - leaving unconfigured
E: gir1.2-webkit-3.0: dependency problems - leaving unconfigured
E: apturl: dependency problems - leaving unconfigured
```

Any ideas?  Thanks

---

### Post by ian-weisser on 2015-09-24
> **exsheeple said:**
> I have check and tried install the system settings 
What is the exact name of the package you are trying to install?
From which source?

---

### Post by exsheeple on 2015-09-24
Im just trying to install system settings.  When I click on the cog gear in the upper right hand corner, the window open to an empty box

---

### Post by grahammechanical on 2015-09-24
Be careful. In the repositories there is a package called systemsettings but that if for KDE and not Ubuntu+gnome+Unity. There is also ubuntu-system-settings but that is for Ubuntu Touch (phone).

What you may be looking for is unity-control-center. Search in Synaptic for unity control center and Synaptic will find it. And then click get screenshot to see if it really is what you are looking for.

Regards

---

### Post by ian-weisser on 2015-09-25
> **exsheeple said:**
> When I click on the cog gear in the upper right hand corner, the window open to an empty box

Did this always occur?
Or is this new?
Do you have any other software that was part of your original install that has disappeared?

Please open a terminal and run the following command.
```
sudo dpkg --configure libgl1-mesa-glx
```
Copy-and-paste the* complete* output here.  [Use [code] tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168") for the output.

---

### Post by exsheeple on 2015-09-25
Thank you to all who replies.  It shows that the unity-control-center is already installed.  Is it possible that something happened during install?

This is a fresh install.  I am not aware of anything else missing except for all the content in the system settings

Response from the command:

dualbooter@Molon-Labe:~$ sudo dpkg --configure libgl1-mesa-glx
[sudo] password for dualbooter: 
Setting up libgl1-mesa-glx:i386 (10.1.3-0ubuntu0.4) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group i386-linux-gnu_gl_conf is broken
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/bin/amdconfig because associated file /usr/lib/fglrx/bin/amdconfig (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/bin/amdnotifyui because associated file /usr/lib/fglrx/bin/amdnotifyui (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /etc/ati because associated file /usr/lib/fglrx/etc/ati (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/bin/aticonfig because associated file /usr/lib/fglrx/bin/aticonfig (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/bin/atieventsd because associated file /usr/lib/fglrx/bin/atieventsd (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/bin/atiodcli because associated file /usr/lib/fglrx/bin/atiodcli (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/bin/atiode because associated file /usr/lib/fglrx/bin/atiode (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/bin/clinfo because associated file /usr/lib/fglrx/bin/clinfo (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/bin/fgl_glxgears because associated file /usr/lib/fglrx/bin/fgl_glxgears (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/lib/dri/fglrx_dri.so because associated file /usr/lib/fglrx/dri/fglrx_dri.so (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /etc/modprobe.d/fglrx.conf because associated file /lib/fglrx/modprobe.conf (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/bin/fglrxinfo because associated file /usr/lib/fglrx/bin/fglrxinfo (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/share/grub-gfxpayload-lists/blacklist/10_proprietary-graphics-drivers because associated file /usr/share/fglrx/fglrx.grub-gfxpayload (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/lib/libAMDXvBA.cap because associated file /usr/lib/fglrx/libAMDXvBA.cap (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/lib/libOpenCL.so because associated file /usr/lib/fglrx/libOpenCL.so (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/lib/libaticalcl.so because associated file /usr/lib/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/lib/libaticalrt.so because associated file /usr/lib/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: error: unable to remove '/etc/ati': Is a directory
dpkg: error processing package libgl1-mesa-glx:i386 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 libgl1-mesa-glx:i386





System Settings
[IMG]http://cloud.1158pm.info/misc/systemsettings.png[/IMG]


Updater before attempted install and fail
[IMG]http://cloud.1158pm.info/misc/updater.png[/IMG]

Stangely, even though i get failed messages, when I go back to try to update, it says Im up to date.....  I just installed a software from the USC and it says failed but it installs the software anyway.....

---

### Post by ian-weisser on 2015-09-25
Yes, you have the right packages.
Your have a configuration error on those updated packages.
Please re-read post #5.

---

### Post by exsheeple on 2015-09-26
Ooops, sorry.

```
dualbooter@Molon-Labe:~$ sudo dpkg --configure libgl1-mesa-glx
[sudo] password for dualbooter: 
Setting up libgl1-mesa-glx:i386 (10.1.3-0ubuntu0.4) ...
update-alternatives: warning: forcing reinstallation of alternative  /usr/lib/fglrx/ld.so.conf because link group i386-linux-gnu_gl_conf is  broken
update-alternatives: warning: skip creation of /usr/bin/amdcccle because  associated file /usr/lib/fglrx/bin/amdcccle (of link group  i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/bin/amdconfig  because associated file /usr/lib/fglrx/bin/amdconfig (of link group  i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/bin/amdnotifyui  because associated file /usr/lib/fglrx/bin/amdnotifyui (of link group  i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of  /etc/OpenCL/vendors/amdocl32.icd because associated file  /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group  i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of  /etc/OpenCL/vendors/amdocl64.icd because associated file  /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group  i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of  /usr/bin/amdupdaterandrconfig because associated file  /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group  i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su  because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group  i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /etc/ati because  associated file /usr/lib/fglrx/etc/ati (of link group  i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/bin/aticonfig  because associated file /usr/lib/fglrx/bin/aticonfig (of link group  i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/bin/atieventsd  because associated file /usr/lib/fglrx/bin/atieventsd (of link group  i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/bin/atiodcli because  associated file /usr/lib/fglrx/bin/atiodcli (of link group  i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/bin/atiode because  associated file /usr/lib/fglrx/bin/atiode (of link group  i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/bin/clinfo because  associated file /usr/lib/fglrx/bin/clinfo (of link group  i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/bin/fgl_glxgears  because associated file /usr/lib/fglrx/bin/fgl_glxgears (of link group  i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/lib/dri/fglrx_dri.so  because associated file /usr/lib/fglrx/dri/fglrx_dri.so (of link group  i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of  /etc/modprobe.d/fglrx.conf because associated file  /lib/fglrx/modprobe.conf (of link group i386-linux-gnu_gl_conf) doesn't  exist
update-alternatives: warning: skip creation of /usr/bin/fglrxinfo  because associated file /usr/lib/fglrx/bin/fglrxinfo (of link group  i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of  /usr/share/grub-gfxpayload-lists/blacklist/10_proprietary-graphics-drivers  because associated file /usr/share/fglrx/fglrx.grub-gfxpayload (of link  group i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/lib/libAMDXvBA.cap  because associated file /usr/lib/fglrx/libAMDXvBA.cap (of link group  i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/lib/libOpenCL.so  because associated file /usr/lib/fglrx/libOpenCL.so (of link group  i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/lib/libaticalcl.so  because associated file /usr/lib/fglrx/libaticalcl.so (of link group  i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so  because associated file /usr/lib32/fglrx/libaticalcl.so (of link group  i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/lib/libaticalrt.so  because associated file /usr/lib/fglrx/libaticalrt.so (of link group  i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so  because associated file /usr/lib32/fglrx/libaticalrt.so (of link group  i386-linux-gnu_gl_conf) doesn't exist
update-alternatives: error: unable to remove '/etc/ati': Is a directory
dpkg: error processing package libgl1-mesa-glx:i386 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 libgl1-mesa-glx:i386
```

---

### Post by ian-weisser on 2015-09-26
Warnings are generally non-critical.
Errors are critical. Here's your only error:
> **exsheeple said:**
> update-alternatives: **error: unable to remove '/etc/ati': Is a directory**
What is in that directory?
Have you been trying to install other graphics drivers? If so, have you been removing them?

---

### Post by exsheeple on 2015-09-26
Once i installed 14.04, there was a hardware driver pop-up and I installed the recommended driver

---

### Post by exsheeple on 2015-09-27
I startpage.com-ed how to remove the ati file.  I
```
sudo apt-get remove --purge ati-*
```
then
```
sudo apt-get update
```
then did an update to make sure all is well.  We will see.  I think I did this right...im still learning Ubuntu.  Thanks everyone for their help

---

### Post by ian-weisser on 2015-09-27
Almost.
Finish your test with:
```
sudo apt-get upgrade
```
*Update* simply updates the dpkg database of all known packages from all your known sources. It doesn't try to deconflict anything.
*Upgrade* tries to apply the latest packages in that database to your system. This is where conflicts are discovered.
You rarely use them separately.

---

### Post by exsheeple on 2015-09-27
Well, something told me not to reboot.  It boots to a black screen, Im using the live CD now.  Is there some way to upgrade from the live CD?

---

### Post by ian-weisser on 2015-09-27
> **exsheeple said:**
> It boots to a black screen

That seems expected. You uninstalled your video drivers, after all.
Can you reach a console to login? (CTRL+ALT+F1)
If not, then backup your data (if any) using your Live Media and then reinstall.

 > **exsheeple said:**
> Is there some way to upgrade from the live CD?

No, unless you are familiar with how to manually mount your hard drive and chroot into it's filesystem.
If you are not experienced with chrooting, this is precisely the wrong time to learn. Backup your data (if any) and reinstall first.

---

### Post by exsheeple on 2015-09-27
Will do.....thanks you all your help

---

