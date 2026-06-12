---
title: "Upgrade error with linux-image-3.11.0-14-generic"
date: 2013-12-19
forum: Installation &amp; Upgrades
---

### Post by nicolargo on 2013-12-19
Hi all,

i have the following error message when i try to update/upgrade my Ubuntu Desktop:

```


[LIST=1]
[*][COLOR=#000000]Paramétrage de linux-image-3.11.0-14-generic (3.11.0-14.21) ...[/COLOR]

[*][COLOR=#000000]Running depmod.[/COLOR]

[*][COLOR=#000000]Failed to run depmod[/COLOR]

[*][COLOR=#000000]dpkg: erreur de traitement de linux-image-3.11.0-14-generic (--configure) :[/COLOR]

[*][COLOR=#000000] le sous-processus script post-installation installé a retourné une erreur de sortie d'état 1[/COLOR]

[*][COLOR=#000000]dpkg: des problèmes de dépendances empêchent la configuration de linux-image-extra-3.11.0-14-generic :[/COLOR]

[*][COLOR=#000000] linux-image-extra-3.11.0-14-generic dépend de linux-image-3.11.0-14-generic ; cependant :[/COLOR]

[*][COLOR=#000000] Le paquet linux-image-3.11.0-14-generic n'est pas encore configuré.[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]dpkg: erreur de traitement de linux-image-extra-3.11.0-14-generic (--configure) :[/COLOR]

[*][COLOR=#000000] problèmes de dépendances - laissé non configuré[/COLOR]

[*][COLOR=#000000]dpkg: des problèmes de dépendances empêchent la configuration de linux-image-generic :[/COLOR]

[*][COLOR=#000000] linux-image-generic dépend de linux-image-3.11.0-14-generic ; cependant :[/COLOR]

[*][COLOR=#000000] Le paquet linux-image-3.11.0-14-generic n'est pas encore configuré.[/COLOR]

[*][COLOR=#000000] linux-image-generic dépend de linux-image-extra-3.11.0-14-generic ; cependant :[/COLOR]

[*][COLOR=#000000] Le paquet linux-image-extra-3.11.0-14-generic n'est pas encore configuré.[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]dpkg: erreur de traitement dAucun rapport « apport » écrit car MaxReports a déjà été atteint[/COLOR]

[*][COLOR=#000000]                                                                                            Aucun rapport « apport » écrit car MaxReports a déjà été atteint[/COLOR]

[*][COLOR=#000000]                                                                                                                                                            Aucun rapport « apport » écrit car MaxReports a déjà été atteint[/COLOR]

[*][COLOR=#000000]                                                    Aucun rapport « apport » écrit car MaxReports a déjà été atteint[/COLOR]

[*][COLOR=#000000]                                                                                                                    e linux-image-generic (--configure) :[/COLOR]

[*][COLOR=#000000] problèmes de dépendances - laissé non configuré[/COLOR]

[*][COLOR=#000000]dpkg: des problèmes de dépendances empêchent la configuration de linux-generic :[/COLOR]

[*][COLOR=#000000] linux-generic dépend de linux-image-generic (= 3.11.0.14.15) ; cependant :[/COLOR]

[*][COLOR=#000000] Le paquet linux-image-generic n'est pas encore configuré.[/COLOR]

[*][COLOR=#000000] [/COLOR]

[*][COLOR=#000000]dpkg: erreur de traitement de linux-generic (--configure) :[/COLOR]

[*][COLOR=#000000] problèmes de dépendances - laissé non configuré[/COLOR]

[*][COLOR=#000000]Des erreurs ont été rencontrées pendant l'exécution :[/COLOR]

[*][COLOR=#000000] linux-image-3.11.0-14-generic[/COLOR]

[*][COLOR=#000000] linux-image-extra-3.11.0-14-generic[/COLOR]

[*][COLOR=#000000] linux-image-generic[/COLOR]

[*][COLOR=#000000] linux-generic[/COLOR]

[*][COLOR=#000000]E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]
[/LIST]

```

My current kernel version is:

```

Linux lifebook 3.11.0-13-generic #20-Ubuntu SMP Wed Oct 23 07:38:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

Additionnaly, here is the syslog after the (failed) upgrade:

```

Dec 19 15:34:16 lifebook whoopsie[1494]: online
Dec 19 15:34:20 lifebook kernel: [31043.074438] ata3.00: exception Emask 0x0 SAct 0x7fffffff SErr 0x40000 action 0x0
Dec 19 15:34:20 lifebook kernel: [31043.074445] ata3.00: irq_stat 0x40000008
Dec 19 15:34:20 lifebook kernel: [31043.074449] ata3: SError: { CommWake }
Dec 19 15:34:20 lifebook kernel: [31043.074453] ata3.00: failed command: READ FPDMA QUEUED
Dec 19 15:34:20 lifebook kernel: [31043.074461] ata3.00: cmd 60/08:00:08:c1:46/00:00:1f:00:00/40 tag 0 ncq 4096 in
Dec 19 15:34:20 lifebook kernel: [31043.074461]          res 41/40:00:0f:c1:46/00:00:1f:00:00/40 Emask 0x409 (media error) <F>
Dec 19 15:34:20 lifebook kernel: [31043.074464] ata3.00: status: { DRDY ERR }
Dec 19 15:34:20 lifebook kernel: [31043.074467] ata3.00: error: { UNC }
Dec 19 15:34:20 lifebook kernel: [31043.074476] ata3: hard resetting link
Dec 19 15:34:21 lifebook kernel: [31043.390893] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 19 15:34:21 lifebook kernel: [31043.392589] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Dec 19 15:34:21 lifebook kernel: [31043.392593] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
Dec 19 15:34:21 lifebook kernel: [31043.439804] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Dec 19 15:34:21 lifebook kernel: [31043.439809] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
Dec 19 15:34:21 lifebook kernel: [31043.440216] ata3.00: configured for UDMA/133
Dec 19 15:34:21 lifebook kernel: [31043.440455] sd 2:0:0:0: [sda] Unhandled sense code
Dec 19 15:34:21 lifebook kernel: [31043.440461] sd 2:0:0:0: [sda]  
Dec 19 15:34:21 lifebook kernel: [31043.440464] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Dec 19 15:34:21 lifebook kernel: [31043.440467] sd 2:0:0:0: [sda]  
Dec 19 15:34:21 lifebook kernel: [31043.440469] Sense Key : Medium Error [current] [descriptor]
Dec 19 15:34:21 lifebook kernel: [31043.440475] Descriptor sense data with sense descriptors (in hex):
Dec 19 15:34:21 lifebook kernel: [31043.440477]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Dec 19 15:34:21 lifebook kernel: [31043.440490]         1f 46 c1 0f 
Dec 19 15:34:21 lifebook kernel: [31043.440496] sd 2:0:0:0: [sda]  
Dec 19 15:34:21 lifebook kernel: [31043.440500] Add. Sense: Unrecovered read error - auto reallocate failed
Dec 19 15:34:21 lifebook kernel: [31043.440503] sd 2:0:0:0: [sda] CDB: 
Dec 19 15:34:21 lifebook kernel: [31043.440505] Read(10): 28 00 1f 46 c1 08 00 00 08 00
Dec 19 15:34:21 lifebook kernel: [31043.440517] end_request: I/O error, dev sda, sector 524730639
Dec 19 15:34:21 lifebook kernel: [31043.440621] ata3: EH complete
Dec 19 15:35:01 lifebook CRON[1908]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Dec 19 15:35:15 lifebook whoopsie[1494]: online
Dec 19 15:35:16 lifebook whoopsie[1494]: online
Dec 19 15:35:59 lifebook kernel: [31141.932727] ata3.00: exception Emask 0x0 SAct 0xfffff SErr 0x40000 action 0x0
Dec 19 15:35:59 lifebook kernel: [31141.932735] ata3.00: irq_stat 0x40000008
Dec 19 15:35:59 lifebook kernel: [31141.932739] ata3: SError: { CommWake }
Dec 19 15:35:59 lifebook kernel: [31141.932743] ata3.00: failed command: READ FPDMA QUEUED
Dec 19 15:35:59 lifebook kernel: [31141.932751] ata3.00: cmd 60/08:00:08:c1:46/00:00:1f:00:00/40 tag 0 ncq 4096 in
Dec 19 15:35:59 lifebook kernel: [31141.932751]          res 41/40:00:0f:c1:46/00:00:1f:00:00/40 Emask 0x409 (media error) <F>
Dec 19 15:35:59 lifebook kernel: [31141.932754] ata3.00: status: { DRDY ERR }

```

I already try:
1) apt-get autoremove
2) apt-get remove linux-image-3.8.0-32-generic + update/upgrade
3) depmod -a
4) apt-get clean + update/upgrade

Any idea :confused:

---

### Post by Bashing-om on 2013-12-19
nicolargo; Hello,

Try this:
```

sudo dpkg --remove linux-generic
sudo apt-get update
sudo apt-get install linux-generic
sudo apt-get dist-upgrade

```
where "dist-upgrade" is the package manager's smart mode to INSTALL a kernel.

[INDENT][INDENT][INDENT]regards
[/INDENT][/INDENT][/INDENT]

---

