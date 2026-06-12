---
title: "New version of Boot Info Script"
date: 2012-04-02
forum: Installation &amp; Upgrades
---

### Post by kansasnoob on 2012-04-02
Hello everyone. I've been busy with Ubuntu +1 so haven't been around much in many months :(

But I just received a message from Gert Hulselmans that I wanted to share with all of you boot problem aficionados. I've not had time to test this yet, and may not have time for a couple of weeks, so hopefully someone else can check this out closely ;)

> Boot Info Script 0.61 is released:

* Add README file.
* Add --update switch to make it easier to download the last development
version.
* Also detect grub2 files when they are located in /grub2 or /boot/grub2.
* Make sure that BIS is run with bash as shell interpreter.
* Added --stdout switch: write results to standard output instead of a file.
* "boot_info_script.sh" file renamed to "bootinfoscript".
* List EFI boot files.
* Fix displaying of config file string for some grub2 (v1.99) binaries.
* New GUIDs added: - new GUID for Linux basic data partition
- Chrome OS partitions
* Check for root rights before checking the list of all needed programs, so
it works also correctly on systems where not all programs are in the $PATH
variable of a normal user.
* Detect if xz or lzma is available on the system (replaces unlzma command).
* Add filesystem info for the detected Windows boot sector code.
* Fix a crash in BIS which occured when processing a modified grub4dos boot
loader file which inserts a SLIC table in the ACPI table. 

The parameters you can use are in the README file and on this download page:

[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)

Also note that BIS now is inside a tar.gz file and when extracted, it should always be executable, so you can finally run BIS more like a regular program (without the bash command in front):

```
sudo ./bootinfoscript
```

Updating to the last git version, works like:

```
./bootinfoscript --update bootinfoscript-git
chmod a+x bootinfoscript-git
```

---

### Post by VMC on 2012-04-02
Yes, this fixes everything so far for me. I had to have 2 or 3 versions of bis depending on whether I had the right compression or gawk installed. 

version 61 takes care of all that.

---

### Post by kansasnoob on 2012-04-02
> **VMC said:**
> Yes, this fixes everything so far for me. I had to have 2 or 3 versions of bis depending on whether I had the right compression or gawk installed. 

version 61 takes care of all that.

Good to hear, thanks for the feedback.

---

### Post by kansasnoob on 2012-04-14
Thought I should bump this to give more eyes a look ;)

---

