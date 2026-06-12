---
title: "dual boot ubuntu server 13.04 with freebsd 10 release"
date: 2014-02-13
forum: Installation &amp; Upgrades
---

### Post by philippe_P on 2014-02-13
Hi,
I have a quad cores personal computer with 500 go harddrive, i have to install freebsd 10 first and after manualy instalation for ubuntu server i386 13.04, ubuntu boot but i cannot to start freebsd system since grub, this my output terminal.



> [COLOR=#000000][FONT=Arial]root@dct-zeus:/home/administrateur# sudo parted /dev/sda unit s print[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Modèle: ATA Hitachi HDP72505 (scsi)
Disque /dev/sda : 976773168s
Taille des secteurs (logiques/physiques): 512B/512B
Table de partitions : gpt[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Numéro  Début       Fin         Taille      Système de fichiers  Nom  Fanions
1      34s         161s        128s                                  démarrage
4      2048s       4095s       2048s                                 bios_grub
2      4096s       385619967s  385615872s  freebsd-ufs
5      385619968s  968884223s  583264256s  ext4
3      968884258s  976773133s  7888876s    linux-swap(v1)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]root@dct-zeus:/home/administrateur#[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]/etc/grub.d/40_custom[/FONT][/COLOR]

> [COLOR=#000000][FONT=Arial]#!/bin/sh[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]exec tail -n +3 $0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]# This file provides an easy way to add custom menu entries.  Simply type the[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]# menu entries you want to add after this comment.  Be careful not to change[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]# the 'exec tail' line above.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]menuentry "FreeBSD 10.0r" {[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]insmod ufs2[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    set root=(hd0,5)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]    kfreebsd [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]}[/FONT][/COLOR]



whish parametres can to write for boot freebsd !

Regards
Philippe

---

