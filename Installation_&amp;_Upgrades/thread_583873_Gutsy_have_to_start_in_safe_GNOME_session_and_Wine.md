---
title: "Gutsy: have to start in safe GNOME session and Wine freezes computer"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Jonathan Métillon on 2007-10-20
Hi,

I just upgraded to Gutsy on my 3 computers.One has two big issues:[LIST=1]
[*]Normal GNOME session won't start. After login in it just freeze to the light-brown empty screen.  I need to shut it down manually.
[*]I can start in safe session mode. Then when trying to launch any Wine application, the whole system totally freeze and I need to shut it down manually.[/LIST]Here's a log starting a Wine application:

```
$ wine /opt/neomule/emule.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
wine: Unhandled page fault on read access to 0x00000348 at address 0x7e0e85ec (thread 0009), starting debugger...
Can't attach process 0008: error 5
```Any idea? :confused:

---

### Post by Jonathan Métillon on 2007-10-20
I just found *[Bug #137735]("https://bugs.launchpad.net/ubuntu/+source/wine/+bug/137735") [gutsy] wine causes hard lockup - every time* and I also have on this computer a *VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video*.

So I commented the following lines in my /etc/X11/xorg.conf:

```
Section "Module"
#       Load    "dri"
#       Load    "glx"
EndSection

#Section "DRI"
#       Mode    0666
#EndSection
```And I restarted but no luck, Wine is still freezing the computer.

My version of Wine is 0.9.46-0ubuntu1

Other related bug and question:

[I][Question #15397]("https://answers.launchpad.net/ubuntu/+question/15397"), Wine on Gutsy freezes PC
[Bug #149609]("https://bugs.launchpad.net/ubuntu/+source/wine/+bug/149609"),         [gutsy] Running a Wine application freezes up the whole system[/I]

---

### Post by Jonathan Métillon on 2007-10-28
Hi,

Since some updates I can now login in GNOME normally, it does not freeze anymore.

But I still can't run any Wine app!

Any idea? :confused:

Does this happen only to people with AMD+VIA computers?

---

