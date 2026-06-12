---
title: "Error installing Ubuntu from Boot stick"
date: 2022-11-22
forum: Installation &amp; Upgrades
---

### Post by turtoise16 on 2022-11-22
Hi,
i tried installing Ubuntu a few times now and whatever i try the following error appears at the i guess last step of the installation:
```
The system log from your installation contains an error. The specific error commonly occurs when there is an issue with the media from which you were installing. (etc)
```
I used Ubuntu 20.04 copied with Rufus first, then with Etcher. With Etcher it looks more decent, no blackscreen on startup, but still the error occurs. The usb stick worked a few days ago when installing Debian and Windows.

When using boot-info i got this link: [https://paste.ubuntu.com/p/sSXC4j5WdW](https://paste.ubuntu.com/p/sSXC4j5WdW)
with boot-repair i get this link: [https://paste.ubuntu.com/p/xD3DB4Bw26](https://paste.ubuntu.com/p/xD3DB4Bw26)

Thank you for any help :)

---

### Post by ActionParsnip on 2022-11-22
Did you MD5 test the ISO you downloaded (or use torrents) to download the ISO you used?
The message says that the install media (The USB stick itself) maybe at fault. Have you tried a different USB stick?

---

### Post by turtoise16 on 2022-11-22
I will try this in today via torrent. Maybe the iso is actually somehow incorrect. The USB stick worked the last days but i will try with a dvd (don t have another usb stick). In the mean time i tried the repair tool to repair it itself and it sais: Error: NVram is locked (Ubuntu not found im efibootmgr). [https://paste.ubuntu.com/p/8cKvd7wVMV](https://paste.ubuntu.com/p/8cKvd7wVMV)

---

### Post by turtoise16 on 2022-11-22
I tried installing with another boot stick and an ubuntu-iso downloaded via torrent. Still the same error. Other ideas?

---

### Post by oldfred on 2022-11-22
[https://ubuntuforums.org/showthread.php?t=2481210](https://ubuntuforums.org/showthread.php?t=2481210)

You have nVidia and need Safe boot and include the restricted extras to install nVidia driver from Ubuntu repository.

If you have installed can you boot to grub menu?
If only one install and UEFI boot, you can press escape right after vendor logo screen & before grub menu would normally appear to get grub menu.

If you have UEFI fast boot on, then you may not have time to press any key. That assumes no system changes & immediately boots. You then need to try "cold" boot or full power down, not a warm reboot & then boot & press correct keys to get into UEFI settings.

If you can get grub menu, then use recovery mode entry, or second line in grub menu. Or manually add nomodeset to grub's linux line. Recovery mode already has nomodeset boot parameter.
Then you can enable networking & install nVidia driver from terminal.
sudo ubuntu-drivers autoinstall

---

### Post by turtoise16 on 2022-11-22
Thank you, but actually i did something else to fix my issue. Somehow the download of the other iso did not work correctly or my computer cannot handle the version 20.04.1. Because what i did was to install the newer version without LTS, the 20.10. and the installer worked perfectly fine. I have no idea if my iso of the 20.04. was corrupt or if it was my laptop but i am happy. :)

---

### Post by oldfred on 2022-11-22
Ubuntu 20.10 Groovy Gorilla
October 22, 2020. expires 2021-07-22

That is end of life.
Better maybe to try 22.04 as it is also LTS.

---

