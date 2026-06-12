---
title: "install ubuntu from usb keeps failing"
date: 2018-09-22
forum: Installation &amp; Upgrades
---

### Post by bhomass on 2018-09-22
I am trying to install ubuntu 18.04 onto a motherboard via an usb stick

On the extract media from cp:///media/filesystem step it kept on failing with the message

file "/usr/lib/python3/dist-packages/curtin/utils.py, line131, in _subp cmd=args)
...tin.util.ProcessExecutionError: Unexpected error while running command.
command: ['sh', '-c', 'mkdir -p "$2" && cd "$2" && rsync -aXHAS --one-file-sstem "$1/" .', '--',
...t code :23
reason : -
stdout: ''
stderror: ''

any one knows how to interpret this?

---

### Post by oldfred on 2018-09-22
I would verify that download was correct or that write to flash drive was correct. 
 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) 

Some have to use different flash drive, different port, or different tool to create flash drive.

What brand/model motherboard? Many need UEFI setting changes and will need boot parameters.

If only UEFI, not BIOS/CSM/Legacy boot.
 UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

---

### Post by bhomass on 2018-09-24
was a bad boot usb stick. working now. Thank you.

---

