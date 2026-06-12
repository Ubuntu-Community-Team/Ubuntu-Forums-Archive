---
title: "Splash Page Loading Loop"
date: 2011-08-23
forum: Installation &amp; Upgrades
---

### Post by Paul F. on 2011-08-23
Hello, so the story goes that I just recently crashed my Ubuntu OS (too much tweaking I guess), and I decided to just get rid of it and check out Kubuntu instead. Well, I tried installing Kubuntu on my Windows 7 OS through Wubi and eventually I got that working, but after that I was only able get Kubuntu working once. The only real change I made to Kubuntu was to add repositories to it because for some reason it didn't come with any. Getting on with it though, what happens now is that it runs fine to the point where it's loading from the splash screen to the login screen, and it seems to be in a never ending loading cycle when it enters the splash screen. When I was experimenting with it earlier I noticed that when I press an arrow key or the meta+letter key it displays this message... 

[ply-boot-splash.c]	remove_displays:Removing node
[ply-boot-splash.c]	remove_displays:removing text displays
[ply-boot-splash.c]	remove_displays:Removing 170x48 text display
[ply-boot-splash.c]	remove_displays:Removing node
[main.c]			show_detailed-splash:Showing detailed splash screen
[main.c]			start_boot_splash:Loading boot splash theme '/lib/plymouth/themes/details/details.plymouth'
[ply-key-file.c]		ply_key_file_load_group:trying to load group Plymouth Theme
[ply-key-file.c]		ply_key_file_load_group:Loading boot splash theme '/lib/plymouth/themes/details/details.plymouth'
[./plugin.c]		create_plugin:creating plugin
[main.c]			start_boot_splash:attaching plugin to event loop
[main.c]			start_boot_splash:attaching progress to plugin
[main.c]			add_displays_and_keyboard_to_boot_splash::setting keyboard on boot splash
[main.c]			add_displays_and_keyboard_to_boot_splash:adding pixel display on boot splash
[main.c]			add_displays_and_keyboard_to_boot_splash:adding text display on boot splash
[ply-terminal.c]		ply_terminal_open:terminal /dev/tty7 is already open
[main.c]			start_boot_splash:showing plugin
[ply-boot-splash.c]	ply_boot_splash_show:showing splash screen 

init: unreadahead-other main process (323) terminated with status 4
fsck from util-linux-ng 2.17.2
/dev/loop0: clean, 96897/1073152 files, 699300/4286464 blocks 
 * Starting network connection manager				[ OK ]
 * Starting mDNS/DNS-SD daemon					[ OK ]
 * Starting CUPS printing spooler/server 				[ OK ]
[ply-keyboard.c]		process_keyboard_input:end escape key handler 

Other than this the computer doesn't want to respond (other than forcing a shutdown :( ) Is there anything I can do or should I just try to install Wubi all over again? 

[Here's extra information that might help ( :confused: ) 

* System information: 

Dell Inspiron: N5010 
	*Processor: Intel Core i3 CPU   M 380 @ 253GHz 2.53 GHz
	*RAM: 4.00 GB
	*System type: 64 bit
        *All hardware is functioning normally 

*OS: Kubuntu 11.04 
*Both the default and backup versions are acting this way
*There might have been error messages that came onscreen while booting into the splash screen but it flashes on the screen and its gone, so I couldn't identify it


]

---

