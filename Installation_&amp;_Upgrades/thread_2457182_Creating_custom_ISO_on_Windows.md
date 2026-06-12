---
title: "Creating custom ISO on Windows"
date: 2021-01-27
forum: Installation &amp; Upgrades
---

### Post by hamstermandk on 2021-01-27
My setup is that I have a Hyper-V for my Virtual machines.

I am running an Ubuntu server in one of the VM's but it was manually installed.
I am in the process of making an unattended installation of Ubuntu - automatically (in a PowerShell script).

I am doing this from a Windows.

I can create the ISO - make it bootable but it won't run the unattended installation.
I am suspecting that the ISO is not made probably and I have tried different tools.
Eg. mkisofs (for Windows).

If anyone have succeeded creating an unattended custom ISO for Ubuntu on Windows I would very much like to know how they did it.

---

### Post by hamstermandk on 2021-02-10
I found out that there is really not much difference between Windows and Linux when creating the ISO. 
Just need to remember to use 

$Image.FileSystemsToCreate = 3

when using the New-IsoFile powershell function.
Found many places like her: [https://www.stephenhackers.co.uk/tag/new-isofile/](https://www.stephenhackers.co.uk/tag/new-isofile/)

---

