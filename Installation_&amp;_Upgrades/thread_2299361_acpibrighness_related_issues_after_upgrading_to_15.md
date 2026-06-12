---
title: "acpi/brighness related issues after upgrading to 15.04."
date: 2015-10-17
forum: Installation &amp; Upgrades
---

### Post by amantripathi4u on 2015-10-17
[COLOR=#111111][FONT=Ubuntu]I have just upgraded to 15.04, after the upgrade screen brightness sets automatically to its maximum after every startup or restart. I had faced this problem before when I installed 14.04 on machine, therefore I tried to fix the issue with the same method I used back then. The method was to edit rc.local file and adding following line to the end of the file:[/FONT][/COLOR]
echo 3 > /sys/class/backlight/acpi_video0/brightness
[COLOR=#111111][FONT=Ubuntu]When it did'nt fixed the issue I used second method, which was to create some /etc/init/fixbrighness.conf file and add:[/FONT][/COLOR]
description "Sets brightness after graphics device is loaded"

start on graphics-device-added
task
exec /bin/echo 3 > /sys/class/backlight/acpi_video/brightness
[COLOR=#111111][FONT=Ubuntu]Now every time I start the pc, there are bunch of dialog boxes appear, saying "[COLOR=#222222][FONT=Verdana]The file file:///sys/devices/pci0000:00/0000:00:02.0/backlight/acpi_video0/brightness does not exist." see[/FONT][/COLOR] screenshot,[click to open]("http://i.stack.imgur.com/6kdPt.jpg"). I checked the file, and there was no acpi_video0 folder. So, I thought this might be happened because my acpi controller is intel_brighness, hence I changed the code. But problem remained same. Also some weird things started to happen, like:grep acpi_video /var/log/Xorg.0.log doesn't give any output.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Please help me to get rid of this problem. Any help is appreciated, Thanks very much in advance[/FONT][/COLOR]

---

