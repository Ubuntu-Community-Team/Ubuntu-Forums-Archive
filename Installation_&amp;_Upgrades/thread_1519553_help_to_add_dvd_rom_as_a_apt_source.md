---
title: "help to add dvd rom as a apt source"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by justwarm on 2010-06-28
i have created 5 dual layer dvds which havefull lucid lynx repository .
but before burning i want to check these dvds to be sure that is they are working fine .
so , i want to mount these .iso files as a dvd source via software source manager . please help to how can i do this .

---

### Post by kalistona on 2010-06-28
1° you do not mount ! you click add and it is all. dvd source are not iso to be mount but only sources as any other source. 

2° best way is using comman line : 'mount' and 'available source' are done properly. 

3° know if it is working before ?
you say to your machine : see this cd, and check for update or download. So it is working on.
Are your repositories rights ? only you know that before ! it is your privates choices no ?

---

### Post by luvr on 2010-06-28
> **justwarm said:**
> so , i want to mount these .iso files as a dvd source via software source manager

I don’t think that you will want to add them to the software source manager, because that would mean you need to keep them around. *(Once they are known to the software sources manager, they will be used as a source for installing software packages, until you manually remove them from the list of software sources again.)*

You could mount an ISO file onto your file system via the *“loop device”*—which would go something like this:
```
sudo mount -o loop,ro *ISO_FILE* *MOUNT_POINT*
```
where:
[LIST][*]The *“loop”* option indicates that you want to use the *“loop device”*—i.e., mount an image file *(instead of an actual device).*
[*]The *“ro”* option will cause the device to be mounted in *“read-only”* mode—just like an actual CD or DVD.
[*]*ISO_FILE* specifies the full path to your ISO file.
[*]*MOUNT_POINT* specifies the full path to the location where you want the ISO file to be mounted. This should be an existing, but empty directory.[/LIST]
Once the ISO file is mounted, you can *“see”* its contents, as if it were a real medium; in a way, the loop device can be used to quickly test if an image file really does look like a valid file system, before you burn it to CD or DVD.

---

### Post by justwarm on 2010-06-29
> **luvr said:**
> I don&#8217;t think that you will want to add them to the software source manager, because that would mean you need to keep them around. *(Once they are known to the software sources manager, they will be used as a source for installing software packages, until you manually remove them from the list of software sources again.)*

You could mount an ISO file onto your file system via the *&#8220;loop device&#8221;*&#8212;which would go something like this:
```
sudo mount -o loop,ro *ISO_FILE* *MOUNT_POINT*
```where:
[LIST]
[*]The *&#8220;loop&#8221;* option indicates that you want to use the *&#8220;loop device&#8221;*&#8212;i.e., mount an image file *(instead of an actual device).*
[*]The *&#8220;ro&#8221;* option will cause the device to be mounted in *&#8220;read-only&#8221;* mode&#8212;just like an actual CD or DVD.
[*]*ISO_FILE* specifies the full path to your ISO file.
[*]*MOUNT_POINT* specifies the full path to the location where you want the ISO file to be mounted. This should be an existing, but empty directory.
[/LIST]
Once the ISO file is mounted, you can *&#8220;see&#8221;* its contents, as if it were a real medium; in a way, the loop device can be used to quickly test if an image file really does look like a valid file system, before you burn it to CD or DVD.

after mounting ubuntu-10.04-2010-06-28-complete-edited-by-TKBros-i386-dvd1.iso (i have mounted that .iso file at /media/ubuntu-10.04-2010-06-28-complete-edited-by-TKBros-i386-dvd1 )via that command which you have said ,  when i tried to add cdrom via software source manger it is showing please insert disc in the drive , after continuing it it is showing 
"Error scanning the CD
E:Failed to mount the cdrom. "
so , i am unable to use that .iso file (it is created according to bobsongs tutorial ) as a apt source .
here i am posting that incidents image

---

### Post by luvr on 2010-06-29
> **justwarm said:**
> "Error scanning the CD
E:Failed to mount the cdrom."
In my opinion, if you try to add a CD or DVD to your software sources in this way, the system assumes that you are referring to a real, physical disc in a real, physical CD or DVD drive. It won&#8217;t find your ISO image file.

Thus, the error indicates that there&#8217;s no disc in your CD or DVD drive&#8212;which makes it obvious why the disc cannot be mounted.

To add your image file as a software source, you will have to select ***&#8220;Add...&#8221;*** (instead of *&#8220;Add CD-ROM...&#8221;*), which will prompt you to: ***&#8220;Enter the complete APT line of the repository that you want to add as source&#8221;***&#8212;something like the following:
```
deb   *file:///path/to/where/the/image/file/was/mounted*   karmic   main multiverse restricted universe
```
(typos notwithstanding).

Personally, I&#8217;m not particularly inclined to use the software sources manager in this way, and I prefer to add such lines directly into the *&#8220;/etc/apt/sources.list&#8221;* myself&#8212;using, e.g., the *&#8220;gedit&#8221;* command, as follows:
[LIST][*]Hit the *<CTRL>-<F2>* key combination;
[*]In the *&#8220;Run Application&#8221;* dialog window, type the following command line:
```
gksudo gedit /etc/apt/sources.list
```
[*]Hit the *<Enter>* key (or click *&#8220;Run&#8221;*).[/LIST]
You can now edit the file in any way you see fit. The potential disadvantage, however, is, that *&#8220;gedit&#8221;* won&#8217;t hold your hand the way the software sources manager does; if you make any mistakes, and perhaps even ruin the file, it&#8217;s entirely your responsibility to repair it.

---

### Post by justwarm on 2010-06-30
> **luvr said:**
> In my opinion, if you try to add a CD or DVD to your software sources in this way, the system assumes that you are referring to a real, physical disc in a real, physical CD or DVD drive. It won’t find your ISO image file.

Thus, the error indicates that there’s no disc in your CD or DVD drive—which makes it obvious why the disc cannot be mounted.

To add your image file as a software source, you will have to select ***“Add...”*** (instead of *“Add CD-ROM...”*), which will prompt you to: ***“Enter the complete APT line of the repository that you want to add as source”***—something like the following:
```
deb   *file:///path/to/where/the/image/file/was/mounted*   karmic   main multiverse restricted universe
```(typos notwithstanding).

Personally, I’m not particularly inclined to use the software sources manager in this way, and I prefer to add such lines directly into the *“/etc/apt/sources.list”* myself—using, e.g., the *“gedit”* command, as follows:
[LIST]
[*]Hit the *<CTRL>-<F2>* key combination;
[*]In the *“Run Application”* dialog window, type the following command line:
```
gksudo gedit /etc/apt/sources.list
```
[*]Hit the *<Enter>* key (or click *“Run”*).
[/LIST]
You can now edit the file in any way you see fit. The potential disadvantage, however, is, that *“gedit”* won’t hold your hand the way the software sources manager does; if you make any mistakes, and perhaps even ruin the file, it’s entirely your responsibility to repair it.

but in karmic & jaunty i was able to do that way . i used to mount .iso files via acetoniso in /media/cdrom folder . and after that software source manager was able to detect the cdrom but it is now doing problem with lucid .

---

### Post by luvr on 2010-06-30
> **justwarm said:**
> but in karmic & jaunty i was able to do that way . i used to mount .iso files via acetoniso in /media/cdrom folder . and after that software source manager was able to detect the cdrom but it is now doing problem with lucid .
I’m afraid I cannot help you with this; I’ve never tried that, and I’m not even sure that it is ***supposed*** to work—it may simply have been sheer coincidence that you could do that under Karmic and Jaunty.

One question, though: Does the mount, as you describe it, still work under Lucid, or does that give you problems as well?

---

### Post by justwarm on 2010-07-03
> **luvr said:**
> I’m afraid I cannot help you with this; I’ve never tried that, and I’m not even sure that it is ***supposed*** to work—it may simply have been sheer coincidence that you could do that under Karmic and Jaunty.

One question, though: Does the mount, as you describe it, still work under Lucid, or does that give you problems as well?

I think lucid's software source manager is a victim of bug as I tried to add real apton cd 's via software source  manager  . but that give the same problem . but it wasn't present in karmic & jaunty . 
so , i tried "```

```sudo apt-cdrom add"
this command . and i was succesful . so, it means that there really is any problem exists in software source manager .  for this cause i have created this script .
but there is steel problem present when i tried to add .iso files as a software sources via the command which you have describe in your early post that is showing same problem .

---

