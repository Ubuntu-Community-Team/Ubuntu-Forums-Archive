---
title: "xserver crashes after latest update"
date: 2009-03-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by troyaner on 2009-03-21
after boot I see black screen with some random colored lines

crash appears somewhere between boot screen, and xserver/gdm
after that system is not responsive to any <Ctrl-Alt-...> ttls or xorg restarts

kernel: 2.6.28-11

did anyone make similar experience?



--Update:

installing KDE, to avoid gdm-errors did not work.

attached result of
```
sudo startx 2> startx2
```

it seemes to be the problem, no idea what to do

---

### Post by zika on 2009-03-22
it seems You have ATI card and fglrx driver. boot in recovery mode and run in Terminal```
sudo aticonfig --initial -f
```
if that doesn't do the trick You might want to revert to most rudimentary video driver with:```
sudo dpkg-reconfigure -phigh xserver-xorg
```but that is the last resort ... maybe You would like to ask again for instructions if the first hint doesn't work. there is a way to unistall fglrx and revert to radeon driver.

---

### Post by troyaner on 2009-03-22
initially he told me, there is no driver installed.

after googling for your hint, the solution was:
Downloading my driver form [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
in my case: 
ATI Radeon Mobility X300 =>ati-driver-installer-9.2-x86.x86_64.run
(also chmod a+x *.run)
then as root:
```
./ati-driver-installer-9.2-x86.x86_64.run --buildpkg Ubuntu/jaunty
dpkg -i *.deb
aticonfig --initial -f
telinit 6

```
after reboot, one need to tweak xorg.conf and avoid to update fglrx-*, libamdxvba1, xorg-driver-fglrx-* too early :D

video is back again (though now i'm googling to restore sound ^^)

thx very much, Zika!!!

---

### Post by emdalton on 2009-04-10
I have the Radeon Mobility X300 card working under Jaunty, by following the directions here: 

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

I had been fiddling around trying to get the fglrx driver working, but I couldn't get the window manager to start-- I'd just get the flashing odd bits of color on the screen. At best, with tweaking, I could get the system to boot into low-graphics mode. After following the directions above (including completely uninstalling fglrx components and manual edits to xorg.conf), I was able to get the system to recognize the video card and according to the tests given on that page, I should have 3D graphics acceleration working:

$ glxinfo |grep direct
direct rendering: Yes

What I really need is to get Daz Studio running under Wine. People have managed this with nVidia cards, but until now, there apparently wasn't a driver that supported 3D acceleration for the ATI Radeon Mobility X300. Again, according to the tests on the page above, that should be ok now.

I started Daz Studio from the command line to see what would happen, and got errors about missing fonts and one missing dll: MSVCP60.dll. I used winetricks to get the core fonts and the missing MSVCP60.dll etc. files, and I'm able to run Daz Studio, i.e. the program launches successfully (although it dumps a string of "fixme" warnings and a few errors to the shell). 

In many ways, Daz Studio appears to be working. However, the central pane, which normally shows a preview of the scene, does not update correctly. If I load content into a scene, I can't see it, and if any other window covers the preview pane, that image stays there until some other window image replaces it. Interestingly, I can render a 3D scene normally, and can save the result.

The errors and warnings are these:

```
$ wine DAZStudio.exe
fixme:imm:ImmReleaseContext (0x10020, 0x13bcb0): stub
err:ole:CoGetClassObject class {82c5ab54-c92c-4d52-aac5-27e25e22604c} not registered
err:ole:CoGetClassObject class {82c5ab54-c92c-4d52-aac5-27e25e22604c} not registered
err:ole:create_server class {82c5ab54-c92c-4d52-aac5-27e25e22604c} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {82c5ab54-c92c-4d52-aac5-27e25e22604c} could be created for context 0x17
err:module:import_dll Library S3Dmouse.dll (which is needed by L"C:\\Program Files\\Daz\\Studio\\plugins\\dzsandio.3dm") not found
err:wgl:internal_SetPixelFormat Invalid iPixelFormat: 47404840
err:wgl:internal_SetPixelFormat Invalid iPixelFormat: 47419104
err:wgl:internal_SetPixelFormat Invalid iPixelFormat: 47428488
err:wgl:internal_SetPixelFormat Invalid iPixelFormat: 47438640
fixme:win:SetLayeredWindowAttributes (0x1016a,0x00000000,127,2): stub!
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
err:ole:RevokeDragDrop invalid hwnd (nil)
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:advapi:GetEffectiveRightsFromAclW 0x2dbec54 0x3a29db1c 0x142e16c - stub
fixme:advapi:GetEffectiveRightsFromAclW 0x2dc0484 0x3a29db1c 0x142e16c - stub
fixme:advapi:GetEffectiveRightsFromAclW 0x2dc083c 0x3a29db1c 0x142e16c - stub
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
3DL INFO: $DELIGHT environment variable is not set
3DL WARNING S2051: cannot find default shader 'defaultsurface'
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
3DL WARNING S2051: cannot find default shader 'defaultsurface'
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd (nil)

```

It seems unlikely to me that all of these are critical. The two that seem most relevant to me are the inability to find S3Dmouse.dll and the $DELIGHT environment variable not being set. But I'm not sure-- what about all those ole errors?

I'm running Jaunty with today's updates, wine from the Ubuntu archive (not WineHQ), and very little else custom on this system. It's a Dell Latitude D610. I don't have any other software running that would test 3D graphics, though I'm willing to try something if anyone wants to suggest a good test application. (Edit: I just installed Blender and it works, though screen refreshes are a little funky. But I can add meshes to a scene, manipulate them in the preview window, and render.)

I'm reasonably comfortable with Unix, as I worked on Solaris for years, but I'm new to running linux on x86 hardware and I have very little experience with wine. Any suggestions would be appreciated. Thanks!

---

