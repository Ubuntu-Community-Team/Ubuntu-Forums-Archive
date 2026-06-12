---
title: "Installation Tutorial For WOW &amp; WINE 64 BIT"
date: 2016-07-07
forum: MINT
---

### Post by cor3y91 on 2016-07-07
[SIZE=2]Latest WINE  & Mint 17.3 as 18 doesnt support propriety drivers as of "yet"
  25 step walkthrough
Just to note: all this information ive gathered here is already out there on the web, its just not all in the same place 
So i thought i would share on how exactly I successfully have wow installed and running nicely with no problems at all.
i take no credit for the codes and commands used here.[/SIZE]

                                                                                                  I wrote this using an Intel/AMD based GPU 64 bits, But may work with others

[LIST]
[*]
                                                                                               Follow these steps to get passed all the errors that arise                      

                                                                                                                      This is my first Tutorial By Corey Ward 
[*] 
[/LIST]
 [SIZE=2]1.[/SIZE][SIZE=2] test for OpenGL support. Simply run a check [/SIZE][SIZE=2]in terminal[/SIZE][SIZE=2] to see if you[/SIZE]
 
[LIST]
[*][SIZE=2]have     OpenGL support: [/SIZE] 
[/LIST]
 [SIZE=2]glxinfo|grep 'direct rendering[/SIZE][SIZE=2]'[/SIZE]
 [SIZE=2]this should say **Yes** if you do have support.
If you get no return , you may still be able to run with directx drivers at a cost of fps just skip the OPENGL parts

2. you can run terminal command -
 glxgears 
run for a couple of mins and gather your mean of FPS and
if you want to give you an idea of how your video card is performing and its FPS for the render, Close it when your done.[/SIZE]
 
 
 [SIZE=2]3 In the terminal type the following:[/SIZE]
 [SIZE=2]open terminal type-  
sudo dpkg --add-architecture i386  [/SIZE] 
 
[SIZE=2]sudo add-apt-repository ppa:ubuntu-wine/ppa -y && sudo apt-get update && sudo apt-get install wine 

[/SIZE]
 [SIZE=2]4[/SIZE][SIZE=2]. in terminal type- winecfg   , install prompted
[/SIZE]
 [SIZE=2]5 install winetricks from the synaptic driver manager[/SIZE]
 
 **[SIZE=2]Troubleshooting a Wine App[/SIZE]**

 [SIZE=2]Sometimes, when running an App one or several of the following can happen:[/SIZE]
 [SIZE=2]Frozen App

[/SIZE][SIZE=2]a [/SIZE][SIZE=2]technique of getting out of a frozen state is killing the X server. To do this firs[/SIZE][SIZE=2]t[/SIZE][SIZE=2] configure it by [/SIZE][SIZE=2]typing in terminal

[/SIZE][SIZE=2]sudo dpkg-reconfigure keyboard-configuration[/SIZE][SIZE=2] 

and on the last option there that talks about killing X, say "YES". This will enable the [/SIZE][SIZE=2]CTRL[/SIZE][SIZE=2]+[/SIZE][SIZE=2]ALT[/SIZE][SIZE=2]+[/SIZE][SIZE=2]BACKSPACE[/SIZE][SIZE=2] combination
[/SIZE][SIZE=2]
[/SIZE][SIZE=2]6. [/SIZE][SIZE=2]open terminal type-  sudo dpkg --add-architecture i386  [/SIZE][SIZE=2]

[/SIZE][SIZE=2]7.[/SIZE][SIZE=2] Again type - 
[/SIZE][SIZE=2]sudo add-apt-repository ppa:wine/wine-builds[/SIZE]
 [SIZE=2]8[/SIZE][SIZE=2]then 
[/SIZE][SIZE=2]sudo apt-get update[/SIZE]
 [SIZE=2]9[/SIZE][SIZE=2] type in terminal -[/SIZE]
 [SIZE=2]
[/SIZE][SIZE=2]sudo apt-get install libtxc-dxtn-s2tc0[/SIZE]
 [SIZE=2]
[/SIZE][SIZE=2]10[/SIZE][SIZE=2]. type -  sudo apt-get install mesa-utils[/SIZE]
 [SIZE=2]sudo apt-get install --install-recommends winehq-devel 

[/SIZE][SIZE=2]11[/SIZE][SIZE=2], type wincfg             accept prompts again.[/SIZE]    [SIZE=2]
     In Wine configuration:[/SIZE]

 [SIZE=2]Applications [/SIZE][SIZE=2]tab

[/SIZE][SIZE=2] - Add applications and set to Windows Version [/SIZE][SIZE=2]to [/SIZE][SIZE=2]"Windows 10": [/SIZE][SIZE=2]for[/SIZE][SIZE=2] Default Settings, Agent.exe [/SIZE][SIZE=2]&[/SIZE][SIZE=2] winemenubuilder.exe , [/SIZE][SIZE=2]add those manually[/SIZE]
 [SIZE=2]Alt mod F2

12 .type winetricks[/SIZE]
 [SIZE=2]
Install a DLL or COMPONENT
[SIZE=2]Install all that I have listed . This covers many games & apps:[/SIZE]
d3dx 10
[SIZE=2]d3dx 11_42
[SIZE=2]d3dx 11_43
[SIZE=2]d3dx9
[SIZE=2]d3dx9_26
[SIZE=2]d3dx_28
[SIZE=2]d3dx_31
[SIZE=2]d3dx_35
[SIZE=2]d3dx_36
[SIZE=2]d3dx_39
[SIZE=2]d3dx_42
[SIZE=2]d3dx_43[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]
[/SIZE]                         
Directx9

vcrun2008
vcrun2010

xact
xact_jun2010
xinput
   
 [SIZE=2]WHEN DONE  open winetricks again[/SIZE]
[SIZE=2]. This time select install a font

                        [SIZE=2]. Install Core fonts only
[/SIZE]
 [SIZE=2]13. [/SIZE][SIZE=2]sudo apt-get install ttf-mscorefonts-installer
[/SIZE]
[SIZE=2]14[/SIZE][SIZE=2], type wincfg      [/SIZE]
[SIZE=2]
[/SIZE][SIZE=2]15[/SIZE][SIZE=2]. This is the longest step, as we have to manually add [/SIZE][SIZE=2]more DLL[/SIZE][SIZE=2] in the tab &#8220;Libraries&#8221; - new [/SIZE][SIZE=2]override for library[/SIZE][SIZE=2]:[/SIZE] 
 
 [SIZE=2]After you add the DLL click the edit button and change parimiter to:
[/SIZE]
 
 [SIZE=2]_(native, builtin)  for _[/SIZE]
[SIZE=2]amstream, atl, crypt32, d3dxof, devenum, dplay, dplayx, dpnaddr, dpnet, dpnhpast, dpnlobby, dxdiagn, hhctrl.ocx, hlink, itss, jscript, mlang, mshtml,msvcirt, msvcm80, msvcm90, msvcp80, msvcp90, msvcr80, msvcr90, msvcrt40, msvcrtd, msxml3, odbc32,odbccp32, quartz, riched20, riched32, rsabase, secur32, shdoclc, shdocvw, softpub, urlmon, wintrust[/SIZE]

[SIZE=2]_(builtin) for_[/SIZE]
[SIZE=2]msi, ole32, oleaut32, olepro32, rpcrt4, wininet[/SIZE]

[SIZE=2]_(native) __for- _ dciman32[/SIZE]
 [SIZE=2]Apply and [/SIZE][SIZE=2]OK[/SIZE][SIZE=2].

[/SIZE][SIZE=2]



[/SIZE][SIZE=2]16[/SIZE][SIZE=2]. [/SIZE][SIZE=2]That's not all. To boost the WoW FPS [/SIZE][SIZE=2]even more[/SIZE][SIZE=2], also perform the following tweak: press ALT + F2, enter "regedit" (without the quotes) and:[/SIZE] 
[LIST]
[*] [SIZE=2]navigate     to *HKEY_CURRENT_USER -> Software -> Wine*, select the     Wine folder and right click it, then select *New -> Key* and     rename the newly created key to "OpenGL" (without the     quotes); [/SIZE] 
[*] [SIZE=2]select     the "OpenGL" key, right click it and select *New ->     String Value;* [/SIZE] 
[*] [SIZE=2]rename     "New Value #1" to "DisabledExtensions" (without     the quotes); [/SIZE] 
[*] [SIZE=2]double click on the     newly created "DisabledExtensions" and enter     "GL_ARB_vertex_buffer_object" (without the quotes) into     the "value" field. [/SIZE] 
[/LIST]
 [SIZE=2]17[/SIZE][SIZE=2].  Close regedit[/SIZE] 
                          [SIZE=2]18[/SIZE][SIZE=2]. now when you check this command it shuld return the latest verion of wine back  to you 

 [/SIZE][SIZE=2]wine --version
[/SIZE]
 19[SIZE=2]. Now open PPA (package manager app in start menu usually)

Search Cata[/SIZE][SIZE=2]ly[/SIZE][SIZE=2]st and [/SIZE][SIZE=2]lets[/SIZE][SIZE=2] install-  [/SIZE][SIZE=2]fglrx-amdcccle
 or the -[/SIZE][SIZE=2]updates version either will do, updates is not as stable
[/SIZE][SIZE=2]
[/SIZE][SIZE=2]search and install-  indicator-cpufreq &#8211; [/SIZE][COLOR=#000000][FONT=Noto Sans][SIZE=2]Indicator applet for displaying and changing CPU frequency on the fly[/SIZE][/FONT][/COLOR][SIZE=2]

close the installer.

20. now go to system settings and [/SIZE][SIZE=2]go to mouse/touchpad and turn of emulate middle click.
 [/SIZE][SIZE=2] open Driver Manager. 

We are going to make sure that A proprietary driver is in use here [/SIZE][SIZE=2]fglrx OR -updates package.[/SIZE][SIZE=2]

Now to the advantages of the proprietary driver:[/SIZE] 
[LIST]
[*] It has far superior 3D     performance, what is also relevant for desktop performance when     using a compositing window manager (Unity uses Compiz, which greatly     relies on 3D acceleration) 
[*] With it the graphics card uses     less power (mainly relevant on laptops) 
[*] It comes with OpenCL support,     meaning that some programs can benefit from the graphics chip (for     instance imagemagick, although I think this feature is disabled on     Ubuntu) 
[*] On some cards, the open source driver does not support     audio output over HDMI, in this case, use the proprietary driver. 
[/LIST]
 Now the disadvantages of the proprietary driver
 
[LIST]
[*] Did I mention that it's less     stable than the open source driver? 
[*] On some systems tearing     artefacts are visible when playing video files (there is a setting     in the Catalyst Control Centre to prevent this, yet it doesn't work     on some systems) 
[*] For some settings one has to use Catalyst Control Centre     instead of Ubuntu System Settings, for instance if you want to     extend the desktop to a second monitor for the first time. 
[/LIST]
 [SIZE=2]21[/SIZE][SIZE=2]. [/SIZE][SIZE=2]Right now you&#8217;ve checked that [/SIZE][SIZE=2]you made sure fglrx or /-updates is selected[/SIZE][SIZE=2],[/SIZE][SIZE=2] you can reboot.


[/SIZE][SIZE=2]22[/SIZE][SIZE=2]. Once your back after your reboot.

Hold ALT&F2 and type indicator-cpufreq

Select your CPU frequency in the task bar


 You can safely open Catalyst Control Centre from the start menu too and tweak to that. 


[/SIZE][SIZE=2],


[/SIZE][SIZE=2]23, Now your all set up and ready to install World of Warcraft just like you would on a windows OS, [/SIZE][SIZE=2]if you have trouble launching exe's right click launch with wine[/SIZE]
[SIZE=2]
24. go ahead and install Battle.net. When asked to log in click the cogwheel in top right (settings) and move the mouse down to expand the menu. Select start in offline mode. [/SIZE]
[SIZE=2]Now go to settings again this time locating inside the general tab, 

25. DISABLE: use Browser Hardware Accelerated Graphics When Available. Restart.  [/SIZE][SIZE=2]


Grats!![/SIZE][SIZE=2]


[/SIZE][SIZE=2]Once you have world of warcraft installed Go to your World of Warcraft wine drive folder, go to the WTF folder and then edit your config.wtf file and add this line at the end (or modify it if already exists): SET gxApi "OpenGL"[/SIZE] This will make your wow.exe use opengl everytime you run it.
  
[/SIZE]

---

### Post by howefield on 2016-07-07
Thread moved to the "*MINT*" forum.

---

### Post by Vondreth on 2016-10-03
Hi, first I have to say that this is a nice compilation and it works.

But...
I would suggest that you change the title of this document. Perhaps to "Installation Tutorial for 32-bit WoW and Wine on 64-bit Linux-Mint or Ubuntu."
Why?
Because what you wrote there is to get Wine 32-bit (i386 structure) working on a 64-bit Linux-Mint system.
When it was indeed a 64 bit wine install, than it should be wine64 or WoW64 (Windows on Windows 64) and amd64 for the structure.
WoW (world of warcraft) and other games will run in 32-bit mode. You can see that when you check in battle.net game settings. (64-bit is greyed out.)

( Read up stuff on these pages if you want to know more: [https://wiki.winehq.org/Building_Wine#64-bit_Packages](https://wiki.winehq.org/Building_Wine#64-bit_Packages) and [https://wiki.winehq.org/Ubuntu](https://wiki.winehq.org/Ubuntu) and [https://wiki.ubuntu.com/MultiarchSpec](https://wiki.ubuntu.com/MultiarchSpec) )


Again, it's not negative meant. But just to warn that the title is a bit misleading.
(Or I'm half asleep and have missed something.) Also a possibility.


And a little typo that you keep repeating: it's winecfg not wincfg. (wincfg is not know. And I guess you mean to open the Wine configuration.)  ;)

---

