---
title: "Package downloaded &amp; installed via Synaptic but can find how to start"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Purple Mouse on 2010-04-30
Hmmmm, Interested in trialing Varkon and used Synaptic Package Manager to download and install. According to the [https://help.ubuntu.com/9.10/add-applications/C/installing.html](https://help.ubuntu.com/9.10/add-applications/C/installing.html) it should be there under 'Applications'. I've looked through them all and no sign of Varkon. I've also tried to see if Varkon was installed so I looked via Ubuntu Software Center under installed software. No sign. Did a file search for Varkon. They are there. So, what am I missing here?

---

### Post by djchandler on 2010-04-30
> **Purple Mouse said:**
> Hmmmm, Interested in trialing Varkon and used Synaptic Package Manager to download and install. According to the [https://help.ubuntu.com/9.10/add-applications/C/installing.html](https://help.ubuntu.com/9.10/add-applications/C/installing.html) it should be there under 'Applications'. I've looked through them all and no sign of Varkon. I've also tried to see if Varkon was installed so I looked via Ubuntu Software Center under installed software. No sign. Did a file search for Varkon. They are there. So, what am I missing here?

Right click on the Varkon file you installed in Synaptic and choose "properties." This will bring up a box with several tabs. One of them will show "Installed Files." The file you want is in /usr/bin. You can create a launcher by right clicking the desktop, choose create launcher, then click the "Browse" button and find the proper file in /usr/bin. The  file name should be something like varkon-(something). You can also create an entry in the application menu using **System>Preferences>Main Menu**.

---

### Post by Purple Mouse on 2010-04-30
Thank you djchandler. Very useful however still no go. I eventually found the executable file in /usr/lib/varkon/xvarkon however nothing happens!?!

---

### Post by Purple Mouse on 2010-04-30
Ahhh ha! I've discovered some behind the scenes tweeking required to make this software function. I'm running blind here so it's going to take a while to work out what is required. If you can help all the faster. eg '!varkon.mbsedit.emulator:        kwrite' would I change kwrite to gedit in my instance?

!***************************************************************
!*
!*    Resources to be used with the english version of
!*    VARKON 1.17 for Linux.
!*
!*    (C)Microform AB 1998
!*
!***************************************************************

!*
!***Text font for menus etc.
!*
varkon.font:                    fixed
!*
!***Resources for f216, "Edit active module in MBS format".
!*
varkon.mbsedit.emulator:        xterm -title MBS-Edit -e
varkon.mbsedit.editor:          vi
!varkon.mbsedit.emulator:        kwrite
!varkon.mbsedit.editor: 
varkon.mbsedit.compiler:        mbsc
varkon.mbsedit.autocompile:     True
varkon.mbsedit.autoexec:        True
!*
!***varkon.html_viewer is used by the help-system to spawn a
!***HTML-browser. If this resource is defined VARKON will send
!***the required helpfile to the browser. If not defined
!***VARKON will display text files in VARKON list windows
!***but HTML files will not be supported.
!*
varkon.html_viewer:              sensible-browser
!*
!***Default graphic window. You may use more if you want.
!*
varkon.grawin_1.geometry:       495x435+125
!varkon.grawin_2.geometry:       495x435+135+10
!varkon.grawin_3.geometry:       495x435+145+20
varkon.margin_left:             50
!*
!***Contents of the graphical window titlebar.
!*
varkon.title.project:           True
varkon.title.jobname:           True
varkon.title.viewname:          True
!*
!***Default toolbar for graphics windows.
!*
varkon.button_1.geometry:       48x20+1+0
varkon.button_1.text:           ZOOM
varkon.button_1.action:         f193

varkon.button_2.geometry:       48x20+1+22
varkon.button_2.text:           Auto
varkon.button_2.action:         f194

varkon.button_3.geometry:       48x20+1+44
varkon.button_3.text:           Scale
varkon.button_3.action:         f188

varkon.button_4.geometry:       48x20+1+66
varkon.button_4.text:           Pan
varkon.button_4.action:         f189

varkon.button_5.geometry:       48x20+1+88
varkon.button_5.text:           Prev
varkon.button_5.action:         f191

varkon.button_6.geometry:       48x20+1+110
varkon.button_6.text:           View
varkon.button_6.action:         f195

varkon.button_7.geometry:       48x20+1+132
varkon.button_7.text:           Levels
varkon.button_7.action:         f197

varkon.button_8.geometry:       48x20+1+154
varkon.button_8.text:           Persp
varkon.button_8.action:         f190

varkon.button_9.geometry:       48x20+1+176
varkon.button_9.text:           Delete
varkon.button_9.action:         f10

varkon.button_10.geometry:      48x20+1+198
varkon.button_10.text:          Run
varkon.button_10.action:        f5

varkon.button_11.geometry:      48x20+1+220
varkon.button_11.text:          Edit-P
varkon.button_11.action:        f170

varkon.button_12.geometry:      48x20+1+242
varkon.button_12.text:          MBS
varkon.button_12.action:        f216

varkon.button_13.geometry:      48x20+1+264
varkon.button_13.text:          Hide
varkon.button_13.action:        f133

varkon.button_14.geometry:      48x20+1+286
varkon.button_14.text:          Dyn-R
varkon.button_14.action:        f200
!*
!***Size, position and title of the rendering window.
!*
varkon.renwin.geometry:         500x400+100+50
varkon.renwin.title:            VARKON Dynamic Rendering
!*
!***Dynamic rendering window button texts.
!*
varkon.renwin.scale:            Scale
varkon.renwin.pan:              Pan
varkon.renwin.rotate:           Rot
varkon.renwin.perspective:      Persp
varkon.renwin.light:            Light
varkon.renwin.poly:             Poly
varkon.renwin.fill:             Shade
varkon.renwin.clip:             Clip
varkon.renwin.close:            Close
!*
!***Default position for the menu window.
!*
varkon.menu.geometry:           +5+5
varkon.menu.title:              MENU
!*
!***Resources for list windows.
!*
varkon.list.geometry:           +100+100
varkon.list.title:              Listing - 
varkon.list.title.jobnam:       True
varkon.list.row:                Row
varkon.list.page:               Page
varkon.list.save:               Save
varkon.list.kill:               Close
varkon.list.printer:            lpr
!*
!***Resources for the error message listwindow.
!*
varkon.error.title:             -----------------ERROR-MESSAGE--------------
!*
!***Resources for input dialogs.
!*
varkon.input.title:             Input
varkon.input.page:              Page
varkon.input.okey:              Ok
varkon.input.reject:            Cancel
varkon.input.on:                On
varkon.input.off:               Off
varkon.input.next:              Next
varkon.input.help:              Help
!*
!***Resources for the alternative popup.
!*
varkon.alternative.geometry:    +50+150
varkon.alternative.title:       Alternative  
!*
!***Resources for the view selection list.
!*
varkon.view.title:              View
!*
!***Resources for the scale dialog.
!*
varkon.scale.title:             Scale
varkon.scale.double:            Double
varkon.scale.half:              Half
!*
!***Resources for the perspective dialog.
!*
varkon.persp.title:             Perspective for view : 
varkon.persp.persp:             True perspective
varkon.persp.dist:              Distance is
!*
!***Resources for the levels dialog.
!*
varkon.level.title:             Levels
varkon.level.blank:             Blank
varkon.level.unblank:           Unblank
varkon.level.list:              List
varkon.level.first:             First level
varkon.level.add:               Additional
varkon.level.forward:           Forward
varkon.level.backward:          Backward
varkon.level.last:              Last level
!*
!***Color for active coordinate system.
!*
varkon.act_csys_pen:            2
!*
!***Varkon system colors.
!*
varkon.background:              Gray
varkon.foreground:              Black
varkon.topShadowColor:          White
varkon.bottomShadowColor:       Black
varkon.highlightColor:          Blue
!*
!***Varkon pen colors.
!*
varkon.color_0:                White
varkon.color_1:                Black
varkon.color_2:                Red
varkon.color_3:                LightGreen
varkon.color_4:                LightBlue
varkon.color_5:                DarkRed
varkon.color_6:                DarkGreen
varkon.color_7:                DarkBlue
varkon.color_8:                Brown
varkon.color_9:                Yellow
varkon.color_10:               Orange
varkon.color_11:               Gray
!*
!***OpenGL-configuration. Currently only
!***rgba-mode is supported on color displays.
!***Doublebuffer makes dynamic shading faster.
!*
varkon.shade.rgba:             True
varkon.shade.doublebuffer:     True
!*
!***OpenGL color- and z-depth. Linux with Mesa
!***sets this automatically. IBM, HP
!***and other workstations may require
!***proper settings here.
!*
!varkon.shade.redbits:         8
!varkon.shade.greenbits:       8
!varkon.shade.bluebits:        8
!varkon.shade.zbits:           16
!*
!***Light sources ambient component.
!*
varkon.shade.ambient.red:      40
varkon.shade.ambient.blue:     40
varkon.shade.ambient.green:    40
!*
!***Light sources diffuse component.
!*
varkon.shade.diffuse.red:      100
varkon.shade.diffuse.blue:     100
varkon.shade.diffuse.green:    100
!*
!***Light sources specular component.
!*
varkon.shade.specular.red:     100
varkon.shade.specular.blue:    100
varkon.shade.specular.green:   100

---

### Post by jkurtisr32 on 2010-08-17
> Thank you djchandler. Very useful however still no go. I eventually  found the executable file in /usr/lib/varkon/xvarkon however nothing  happens!?! 	

I think all you have to do is right click on the desktop and create a launcher. You'll find the file for the launcher in /usr/bin.

Worked for me, but this program is not nearly as powerful as something like AutoCAD. I'm wondering id AutoCAD would work in something like Virtual Machine? I might have to dual-boot if VM doesn't work...

---

