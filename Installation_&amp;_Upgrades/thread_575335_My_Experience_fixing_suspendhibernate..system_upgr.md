---
title: "My Experience fixing suspend/hibernate..system upgrade question too."
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by youngilaboungi on 2007-10-13
ok, first, spent a day fixing the blank screen on wake and/or cursor with small square of coulours on black screen.

hibernation and suspend worked after tweaking ill mention, but that's on a clean installation with no system update and with restricted drivers and with uswsusp...but uptil now desktop effects cannot be enabled..
AFTER UPDATE, with restricted nvidia driver i get suspend to work but not hibernate...with ENVY drivers i get hibernate to work but not sleep

ok so this is my experience...or my log of steps showing when they worked and how they stopped working after system update of 190MB....

can someone tell me which of the updates i should disable to make everything fine again? and how to fix desktop effects enabling?

sorry for the long post..i just thought someone can learn from a log type steps to show what affects what.

oh and i have HP pavilion dv6395ea 2GHZ centrino duo, 2 GB RAM, 160 GB HDD, Feisty fawn 7.04.
----------------------------------------------------------------


Suspend/Hibernate function fix.

...that's on Feisty..lots of people complained about suspend/hibernation not working after upgrading to Feisty.
If you don't get it working like my method try upgrade to 7.10 ubuntu should be out this week.

1- Copy following text:

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

# Save and restore video state?
SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=false

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="mysql "

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false


2-Open terminal,

sudo gedit /etc/default/acpi-support

3- Ctrl+A then paste over it the previous text.

installed "hibernate" from synaptic packages.

ok, uptil here got hibernation working with nvidia restricted drivers that is detected automatically from ubuntu upon new clean installation, but no sleep


I tried to disable ohci1394 (which is firewire driver by adding: Blacklist ohci1394) because of the error "ohci1394 does not fully support suspend" but still didnt get suspend to work.

installed uswsusp caused hibernate and sleep not to work, uninstalled remove completely and got hibernation back.

testing desktop effects if would affect hibernation, prompted for enablind nvidia drivers(it was in use at restrickted drivers but not enabled!!) so that prompted to make package download of nvidia-glx and remove of glx-new.

asked for reboot to activate the new drivers. after reboot, pc could not hibernate properly but sleep worked fine.

allowing desktop effects to see what it would affect...desktop effects could not be enabled was prompted.

reinstalled uswsusp...and as before, sudo s2ram not working, but sudo s2ram -fsmp does sleep and this time it worked fine not as before. sudo s2disk WORKED!!...perfect, now i have sleep and hibernation working with uswsusp.

trying hibernate without s2disk, just normally from gdm. this time no hang, just screen going blank black and prompt for login with no hibernation.

sudo s2ram shows error of machine not known or something like that... s2ram -f works perfectly as well as s2ram --force , and s2ram -fsmp .


########Trying to make uswsusp the default.:  files available at: [http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)

1- edit the suspend file "hal-system-power-suspen-linux"
2-find and edit  if [ -x "/sbin/s2ram" ] ; then
	          /sbin/s2ram

to: if [ -x "/sbin/s2ram" ] ; then
	    /sbin/s2ram -f

3- copy the 2 scripts files of suspend and hibernate to their correct location.
sudo cp /path/of_file/hal-system-power-hibernation-linux /usr/lib/hal/scripts/linux/
sudo cp /path/of_file/hal-system-power-suspend-linux /usr/lib/hal/scripts/linux/
sudo chmod 755 /usr/lib/hal/scripts/linux/*


testing hibernation from gdm after setting default.

gdm suspend works after setting in default files "s2ram -f" to override the machine not known issue. hibernation working from gdm too.

SUCCESS!!

This is what i did to get it working, maybe there's something in the sequence that is not the cause of it working but, but whatever and i dont care as long as it's working and have no problem but desktop effects.

doing system upgrade to see if i'll get suspend with it.

All this was done from a clean installation of ubuntu 7.04 downloaded from ubuntu.com, and no upgrade packaged gotten from prompted update after installation.

will try to see if everything works fine after installation of system updates.

yesterday, i had compiz fusion along with emerald theme manager installed, but only got suspend to work (hibernation didnt work) and that's only when effects are disabled.

blacklist of intel_agp to test...nothing new

going to restricted drivers, found nvidia driver enabled, disabling it makes suspend not work, but hibernate work...putting it back enabled makes suspend work but hibernate no.

edited /etc/modules adding "nvidia" on top

2 updates available..kernel updates...checking what they would affect...nothing new.


system update with all packages is done, sleep works perfectly, hibernation hangs without actually hibernating system, reboot is a must....reason is nvidia restricted drivers enabled making sleep work but not hibernation.
------------------------------------------------------------

Update nVidia drivers like following:

1- download and execute: 
[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb)

2-  * Start Envy. It can be found here: Applications -> System Tools -> Envy
    * Select the correct video card vendor and click on Apply:
    * You will see a terminal window that's installing the lastest driver for you card. 
    * You'll get 2 dialog boxes.

      Click yes to have it rewrite the xorg.conf file

      Click yes again to reboot

Your machine will start to reboot.

3-from application>system tools>nvidia  be sure to disable "sync to VBlank"

4-edit xorg.conf file to make suspend work, from terminal enter codes:

sudo gedit /etc/X11/xorg.conf

5-add the following to section "device" while making sure Driver is "nvidia" not "nv"

    Option "NoLogo" "True"
    Option "RenderAccel" "True"
    Option "AddARGBGLXVisuals" "False"
    Option "AllowGLXWithComposite" "False"
    Option          "NvAGP"       "1"

if you're not using the ENVY installed drivers, and restricted drivers of linux are the ones working, then i experienced changing "nv" to "nvidia" caused X server not to boot.

anyway if that happens, get to console then write: nano /etc/X11/xorg.conf  to edit the file back in console.

when ENVY installed and restricted nvidia drivers disabled i get working hibernation but no suspend.

---

### Post by youngilaboungi on 2007-10-13
so before upgrade i had all working but desktop effects...after upgrade of 190 MB either hibernation or sleep work according to which driver in use.

---

