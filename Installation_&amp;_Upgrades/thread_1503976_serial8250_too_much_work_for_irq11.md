---
title: "serial8250: too much work for irq11"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by borderfox on 2010-06-07
I'm after installing Ubuntu 10.04 and I want to access a usb card reader - ideally through a usb hub - but whether i slot the reader in directly or through the hub, i'm getting irq related errors (see dmesg output below).  I've tried to look this up and the only suggestion I could find was to change the irq settings in bios.  However, my bios version doesn't facilitate this option. 

Has anyone else encountered this issue?
If so, how did you overcome it??

```
[   30.098941] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.098950] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.098967] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 04 00 00 02 00
[   30.098981] end_request: I/O error, dev sr1, sector 16
[   30.212719] serial8250: too much work for irq11
[   30.213922] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.213931] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.213938] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.213946] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.213963] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[   30.213977] end_request: I/O error, dev sr1, sector 128
[   30.220129] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.220139] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.220146] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.220155] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.220171] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[   30.220185] end_request: I/O error, dev sr1, sector 128
[   30.226092] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.226104] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.226111] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.226120] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.226138] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[   30.226152] end_request: I/O error, dev sr1, sector 128
[   30.232146] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.232156] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.232162] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.232170] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.232185] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 04 00 00 02 00
[   30.232199] end_request: I/O error, dev sr1, sector 16
[   30.238100] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.238109] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.238116] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.238124] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.238140] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[   30.238153] end_request: I/O error, dev sr1, sector 128
[   30.244138] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.244150] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.244157] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.244165] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.244184] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[   30.244197] end_request: I/O error, dev sr1, sector 64
[   30.250097] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.250107] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.250114] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.250122] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.250139] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[   30.250152] end_request: I/O error, dev sr1, sector 64
[   30.256290] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.256301] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.256307] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.256316] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.256333] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[   30.256347] end_request: I/O error, dev sr1, sector 64
[   30.262118] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.262129] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.262136] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.262144] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.262161] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[   30.262174] end_request: I/O error, dev sr1, sector 64
[   30.268156] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.268165] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.268172] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.268180] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.268195] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[   30.268209] end_request: I/O error, dev sr1, sector 64
[   30.383298] serial8250: too much work for irq11
[   30.383483] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.383488] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.383495] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.383503] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.383520] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[   30.383534] end_request: I/O error, dev sr1, sector 64
[   30.386298] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.386308] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.386314] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.386322] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.386338] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[   30.386351] end_request: I/O error, dev sr1, sector 64
[   30.392287] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.392297] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.392304] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.392312] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.392329] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[   30.392343] end_request: I/O error, dev sr1, sector 64
[   30.398300] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.398310] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.398317] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.398325] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.398340] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[   30.398354] end_request: I/O error, dev sr1, sector 64
[   30.404360] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.404370] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.404377] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.404385] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.404401] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[   30.404415] end_request: I/O error, dev sr1, sector 64
[   30.410333] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.410344] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.410350] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.410359] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.410373] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 40 00 00 02 00
[   30.410387] end_request: I/O error, dev sr1, sector 256
[   30.416333] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.416343] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.416350] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.416358] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.416376] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 40 00 00 02 00
[   30.416390] end_request: I/O error, dev sr1, sector 256
[   30.422337] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.422347] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.422354] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.422362] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.422378] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 42 00 00 02 00
[   30.422391] end_request: I/O error, dev sr1, sector 264
[   30.428407] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.428418] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.428425] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.428434] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.428450] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 42 00 00 02 00
[   30.428464] end_request: I/O error, dev sr1, sector 264
[   30.434356] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.434366] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.434373] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.434381] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.434397] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 44 00 00 02 00
[   30.434410] end_request: I/O error, dev sr1, sector 272
[   30.440349] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.440359] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.440366] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.440374] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.440391] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 44 00 00 02 00
[   30.440405] end_request: I/O error, dev sr1, sector 272
[   30.446371] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.446381] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.446388] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.446395] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.446412] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 c0 00 00 02 00
[   30.446426] end_request: I/O error, dev sr1, sector 768
[   30.452394] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.452403] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.452410] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.452418] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.452433] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 c0 00 00 02 00
[   30.452447] end_request: I/O error, dev sr1, sector 768
[   30.458389] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.458399] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.458405] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.458414] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.458430] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 c2 00 00 02 00
[   30.458443] end_request: I/O error, dev sr1, sector 776
[   30.464362] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.464371] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.464378] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.464386] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.464404] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 c2 00 00 02 00
[   30.464418] end_request: I/O error, dev sr1, sector 776
[   30.470378] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.470388] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.470395] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.470403] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.470418] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 c4 00 00 02 00
[   30.470432] end_request: I/O error, dev sr1, sector 784
[   30.476478] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.476487] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.476494] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.476502] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.476518] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 c4 00 00 02 00
[   30.476531] end_request: I/O error, dev sr1, sector 784
[   30.482423] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.482433] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.482440] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.482448] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.482463] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   30.482476] end_request: I/O error, dev sr1, sector 0
[   30.488577] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.488587] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.488593] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.488601] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.488617] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   30.488630] end_request: I/O error, dev sr1, sector 0
[   30.494440] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.494450] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.494457] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.494465] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.494481] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   30.494495] end_request: I/O error, dev sr1, sector 0
[   30.500520] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.500530] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.500537] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.500545] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.500562] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   30.500576] end_request: I/O error, dev sr1, sector 0
[   30.506569] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.506579] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.506585] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.506593] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.506609] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   30.506622] end_request: I/O error, dev sr1, sector 0
[   30.512503] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.512512] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.512519] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.512527] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.512542] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 04 00 00 02 00
[   30.512556] end_request: I/O error, dev sr1, sector 16
[   30.518540] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.518551] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.518557] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.518565] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.518581] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   30.518595] end_request: I/O error, dev sr1, sector 0
[   30.524547] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.524557] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.524563] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.524572] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.524588] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   30.524601] end_request: I/O error, dev sr1, sector 0
[   30.530486] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.530496] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.530503] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.530511] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.530527] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   30.530540] end_request: I/O error, dev sr1, sector 0
[   30.536555] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.536565] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.536572] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.536580] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.536596] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   30.536609] end_request: I/O error, dev sr1, sector 0
[   30.542543] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.542552] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.542559] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.542566] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.542582] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   30.542596] end_request: I/O error, dev sr1, sector 0
[   30.548583] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.548593] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.548600] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.548608] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.548626] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   30.548639] end_request: I/O error, dev sr1, sector 0
[   30.554503] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.554513] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.554520] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.554529] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.554546] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   30.554560] end_request: I/O error, dev sr1, sector 0
[   30.560563] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.560573] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.560579] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.560587] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.560603] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   30.560617] end_request: I/O error, dev sr1, sector 0
[   30.566538] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.566548] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.566555] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.566563] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.566579] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   30.566593] end_request: I/O error, dev sr1, sector 0
[   30.572736] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.572747] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.572753] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.572762] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.572779] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   30.572793] end_request: I/O error, dev sr1, sector 0
[   30.578512] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.578522] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.578529] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.578536] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.578551] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   30.578565] end_request: I/O error, dev sr1, sector 0
[   30.584744] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.584755] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.584761] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.584770] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.584786] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   30.584799] end_request: I/O error, dev sr1, sector 0
[   30.590602] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.590614] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.590620] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.590629] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.590644] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[   30.590658] end_request: I/O error, dev sr1, sector 128
[   30.596627] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.596636] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.596643] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.596651] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.596667] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[   30.596680] end_request: I/O error, dev sr1, sector 128
[   30.602576] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.602586] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.602593] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.602601] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.602616] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 04 00 00 02 00
[   30.602630] end_request: I/O error, dev sr1, sector 16
[   30.608626] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.608635] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.608641] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.608649] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.608665] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   30.608679] end_request: I/O error, dev sr1, sector 0
[   30.614643] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.614652] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.614659] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.614667] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.614683] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   30.614696] end_request: I/O error, dev sr1, sector 0
[   30.622400] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.622413] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.622419] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.622428] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.622444] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 02 00 00 02 00
[   30.622458] end_request: I/O error, dev sr1, sector 8
[   30.627653] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.627664] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.627671] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.627679] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.627694] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 04 00 00 02 00
[   30.627708] end_request: I/O error, dev sr1, sector 16
[   30.633760] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.633771] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.633778] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.633787] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.633802] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   30.633817] end_request: I/O error, dev sr1, sector 0
[   30.639633] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.639644] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.639652] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.639660] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.639677] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   30.639691] end_request: I/O error, dev sr1, sector 0
[   30.645621] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.645631] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.645637] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.645645] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.645661] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   30.645674] end_request: I/O error, dev sr1, sector 0
[   30.651656] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.651667] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.651673] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.651681] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.651697] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   30.651710] end_request: I/O error, dev sr1, sector 0
[   30.658215] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.658227] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.658234] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.658242] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.658259] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   30.658272] end_request: I/O error, dev sr1, sector 0
[   30.663639] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.663648] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.663655] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.663663] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.663679] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   30.663693] end_request: I/O error, dev sr1, sector 0
[   30.669678] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.669688] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.669695] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.669704] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.669721] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 02 00 00 02 00
[   30.669735] end_request: I/O error, dev sr1, sector 8
[   30.675672] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.675682] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.675689] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.675697] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.675712] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[   30.675726] end_request: I/O error, dev sr1, sector 128
[   30.681640] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.681649] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.681656] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.681664] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.681679] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   30.681693] end_request: I/O error, dev sr1, sector 0
[   30.687628] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.687639] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.687646] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.687654] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.687670] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   30.687683] end_request: I/O error, dev sr1, sector 0
[   30.693673] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.693682] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.693689] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.693697] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.693712] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 04 00 00 00 02 00
[   30.693726] end_request: I/O error, dev sr1, sector 4096
[   30.705714] sr1: CDROM (ioctl) error, command: Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 00
[   30.705744] sr: Sense Key : Medium Error [current] 
[   30.705750] sr: Add. Sense: Unable to recover table-of-contents
[   30.719696] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.719705] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.719712] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.719720] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.719735] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   30.719748] end_request: I/O error, dev sr1, sector 0
[   30.725735] sr 1:0:1:0: [sr1] Unhandled sense code
[   30.725747] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   30.725754] sr 1:0:1:0: [sr1] Sense Key : Medium Error [current] 
[   30.725762] sr 1:0:1:0: [sr1] Add. Sense: Unable to recover table-of-contents
[   30.725776] sr 1:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[   30.725790] end_request: I/O error, dev sr1, sector 0
[   45.252316] serial8250: too much work for irq11
[   45.423033] serial8250: too much work for irq11
[   45.593826] serial8250: too much work for irq11
[   45.764528] serial8250: too much work for irq11
[   45.935266] serial8250: too much work for irq11
[   45.968065] end_request: I/O error, dev fd0, sector 0
[   46.106178] serial8250: too much work for irq11
[   46.124111] end_request: I/O error, dev fd0, sector 0
[   46.276840] serial8250: too much work for irq11
[   46.447571] serial8250: too much work for irq11
[   46.618340] serial8250: too much work for irq11
[   46.789102] serial8250: too much work for irq11
[   46.959899] serial8250: too much work for irq11
[   47.130576] serial8250: too much work for irq11
[   47.301407] serial8250: too much work for irq11
[   47.472863] serial8250: too much work for irq11
[   47.643383] serial8250: too much work for irq11
[   47.814068] serial8250: too much work for irq11
[   47.985132] serial8250: too much work for irq11
[   48.155721] serial8250: too much work for irq11
[   48.326449] serial8250: too much work for irq11
[   48.497366] serial8250: too much work for irq11
[   48.667928] serial8250: too much work for irq11
[   48.838270] serial8250: too much work for irq11
[   49.009459] serial8250: too much work for irq11
[   49.179729] serial8250: too much work for irq11
[   49.350510] serial8250: too much work for irq11
[   49.521445] serial8250: too much work for irq11
[   49.692235] serial8250: too much work for irq11
[   49.862759] serial8250: too much work for irq11
[   50.033596] serial8250: too much work for irq11
[   50.204311] serial8250: too much work for irq11
[   50.375050] serial8250: too much work for irq11
[   50.545899] serial8250: too much work for irq11
[   50.716665] serial8250: too much work for irq11
[   50.887313] serial8250: too much work for irq11
[   51.058080] serial8250: too much work for irq11
[   51.228853] serial8250: too much work for irq11
[   51.399658] serial8250: too much work for irq11
[   51.570361] serial8250: too much work for irq11
[   51.741208] serial8250: too much work for irq11
[   51.911891] serial8250: too much work for irq11
[   52.082650] serial8250: too much work for irq11
[   52.253447] serial8250: too much work for irq11
[   52.424162] serial8250: too much work for irq11
[   52.594977] serial8250: too much work for irq11
[   52.765752] serial8250: too much work for irq11
[   52.936470] serial8250: too much work for irq11
[   53.107225] serial8250: too much work for irq11
[   53.277968] serial8250: too much work for irq11
[   53.448759] serial8250: too much work for irq11
[   53.619503] serial8250: too much work for irq11
[   53.790255] serial8250: too much work for irq11
[   53.961051] serial8250: too much work for irq11
[   54.131760] serial8250: too much work for irq11
[   54.302526] serial8250: too much work for irq11
[   54.473327] serial8250: too much work for irq11
[   54.644110] serial8250: too much work for irq11
[   54.814823] serial8250: too much work for irq11
[   54.985652] serial8250: too much work for irq11
borderfox@borderfox-desktop:~$
```

---

### Post by borderfox on 2010-06-07
Some of the errors in the above dmesg have been overcome (see below) -  just leaving the irq issue...
```
[    1.219329] io scheduler deadline registered
[    1.219415] io scheduler cfq registered (default)
[    1.219649] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.219690] pciehp: PCI Express Hot Plug Controller Driver version:  0.4
[    1.219909] input: Sleep Button as  /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    1.219928] ACPI: Sleep Button [SLPB]
[    1.220012] input: Power Button as  /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    1.220017] ACPI: Power Button [PWRF]
[    1.220277] processor LNXCPU:00: registered as cooling_device0
[    1.229017] isapnp: Scanning for PnP cards...
[    1.279471] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.279640] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.279776] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.280239] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.280425] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.280959] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    1.280966] PCI: setting IRQ 11 as level-triggered
[    1.280974] serial 0000:00:0d.0: PCI INT A -> Link[LNKC] -> GSI  11 (level, low) -> IRQ 11
[    1.281152] 0000:00:0d.0: ttyS2 at I/O 0xc808 (irq = 11) is a 16450
[    1.281251] 0000:00:0d.0: ttyS3 at I/O 0xc810 (irq = 11) is a 8250
[    1.281288] Couldn't register serial port 0000:00:0d.0: -28
[    1.287333] brd: module loaded
[    1.288270] loop: module loaded
[    1.288526] input: Macintosh mouse button emulation as  /devices/virtual/input/input2
[    1.288854] pata_sis 0000:00:02.5: version 0.5.2
[    1.290945] scsi0 : pata_sis
[    1.295164] scsi1 : pata_sis
[    1.297296] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00  irq 14
[    1.297303] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08  irq 15
[    1.297995] Fixed MDIO Bus: probed
[    1.298058] PPP generic driver version 2.4.2
[    1.298234] tun: Universal TUN/TAP device driver, 1.6
[    1.298238] tun: (C) 1999-2004 Max Krasnyansky  <maxk@qualcomm.com>
[    1.298430] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI)  Driver
[    1.298481] ehci_hcd 0000:00:09.2: PCI INT C -> Link[LNKC] ->  GSI 11 (level, low) -> IRQ 11
[    1.298522] ehci_hcd 0000:00:09.2: EHCI Host Controller
[    1.298585] ehci_hcd 0000:00:09.2: new USB bus registered, assigned  bus number 1
[    1.298980] ehci_hcd 0000:00:09.2: irq 11, io mem 0xcfffdf00
[    1.311101] ehci_hcd 0000:00:09.2: USB 2.0 started, EHCI 0.95
[    1.311452] usb usb1: configuration #1 chosen from 1 choice
[    1.311514] hub 1-0:1.0: USB hub found
[    1.311554] hub 1-0:1.0: 4 ports detected
[    1.311671] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.312113] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    1.312121] ohci_hcd 0000:00:02.2: PCI INT D -> Link[LNKD] ->  GSI 11 (level, low) -> IRQ 11
[    1.312164] ohci_hcd 0000:00:02.2: OHCI Host Controller
[    1.312250] ohci_hcd 0000:00:02.2: new USB bus registered, assigned  bus number 2
[    1.312294] ohci_hcd 0000:00:02.2: irq 11, io mem 0xcfffe000
[    1.384961] usb usb2: configuration #1 chosen from 1 choice
[    1.385026] hub 2-0:1.0: USB hub found
[    1.385056] hub 2-0:1.0: 3 ports detected
[    1.385548] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 12
[    1.385554] PCI: setting IRQ 12 as level-triggered
[    1.385562] ohci_hcd 0000:00:02.3: PCI INT A -> Link[LNKH] ->  GSI 12 (level, low) -> IRQ 12
[    1.385602] ohci_hcd 0000:00:02.3: OHCI Host Controller
[    1.385689] ohci_hcd 0000:00:02.3: new USB bus registered, assigned  bus number 3
[    1.385735] ohci_hcd 0000:00:02.3: irq 12, io mem 0xcffff000
[    1.476582] usb usb3: configuration #1 chosen from 1 choice
[    1.476647] hub 3-0:1.0: USB hub found
[    1.476684] hub 3-0:1.0: 3 ports detected
[    1.476821] uhci_hcd: USB Universal Host Controller Interface driver
[    1.477348] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 5
[    1.477354] PCI: setting IRQ 5 as level-triggered
[    1.477362] uhci_hcd 0000:00:09.0: PCI INT A -> Link[LNKA] ->  GSI 5 (level, low) -> IRQ 5
[    1.477379] uhci_hcd 0000:00:09.0: UHCI Host Controller
[    1.477473] uhci_hcd 0000:00:09.0: new USB bus registered, assigned  bus number 4
[    1.477518] uhci_hcd 0000:00:09.0: irq 5, io base 0x0000d000
[    1.477737] usb usb4: configuration #1 chosen from 1 choice
[    1.477786] hub 4-0:1.0: USB hub found
[    1.477806] hub 4-0:1.0: 2 ports detected
[    1.478144] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 12
[    1.478151] uhci_hcd 0000:00:09.1: PCI INT B -> Link[LNKB] ->  GSI 12 (level, low) -> IRQ 12
[    1.478162] uhci_hcd 0000:00:09.1: UHCI Host Controller
[    1.478244] uhci_hcd 0000:00:09.1: new USB bus registered, assigned  bus number 5
[    1.478273] uhci_hcd 0000:00:09.1: irq 12, io base 0x0000d400
[    1.478453] usb usb5: configuration #1 chosen from 1 choice
[    1.478509] hub 5-0:1.0: USB hub found
[    1.478528] hub 5-0:1.0: 2 ports detected
[    1.483210] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.483219] PNP: PS/2 appears to have AUX port disabled, if this is  incorrect please boot with i8042.nopnp
[    1.483453] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.483769] mice: PS/2 mouse device common for all mice
[    1.484102] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.484130] rtc0: alarms up to one month, 114 bytes nvram
[    1.484333] device-mapper: uevent: version 1.0.3
[    1.488045] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01)  initialised: dm-devel@redhat.com
[    1.488233] device-mapper: multipath: version 1.1.0 loaded
[    1.488239] device-mapper: multipath round-robin: version 1.0.0  loaded
[    1.491153] EISA: Probing bus 0 at eisa.0
[    1.491200] EISA: Detected 0 cards.
[    1.494586] cpuidle: using governor ladder
[    1.494596] cpuidle: using governor menu
[    1.495489] TCP cubic registered
[    1.495746] NET: Registered protocol family 10
[    1.496476] lo: Disabled Privacy Extensions
[    1.496949] NET: Registered protocol family 17
[    1.497519] ata1.00: ATA-7: SAMSUNG SP1604N, TM100-24, max UDMA/100
[    1.497524] ata1.00: 312581808 sectors, multi 16: LBA48 
[    1.497689] ata1.01: ATA-7: SAMSUNG SP1604N, TM100-24, max UDMA/100
[    1.497694] ata1.01: 312581808 sectors, multi 16: LBA48 
[    1.498029] powernow-k8: Processor cpuid 681 not supported
[    1.498080] Using IPI No-Shortcut mode
[    1.498303] PM: Resume from disk failed.
[    1.498335] registered taskstats version 1
[    1.498731]   Magic number: 14:457:792
[    1.498924] rtc_cmos 00:02: setting system clock to 2010-06-07  16:46:42 UTC (1275929202)
[    1.498930] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.498933] EDD information not available.
[    1.503208] input: AT Translated Set 2 keyboard as  /devices/platform/i8042/serio0/input/input3
[    1.503571] ata1.00: configured for UDMA/100
[    1.511487] ata1.01: configured for UDMA/100
[    1.662610] usb 1-1: new high speed USB device using ehci_hcd and  address 2
[    1.854435] usb 1-1: configuration #1 chosen from 1 choice
[    1.855194] hub 1-1:1.0: USB hub found
[    1.855817] hub 1-1:1.0: 4 ports detected
[    1.922455] isapnp: No Plug & Play device found
[    1.922910] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG SP1604N   TM10 PQ: 0 ANSI: 5
[    1.923314] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.923525] scsi 0:0:1:0: Direct-Access     ATA      SAMSUNG SP1604N   TM10 PQ: 0 ANSI: 5
[    1.923713] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    1.923998] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160  GB/149 GiB)
[    1.924096] sd 0:0:0:0: [sda] Write Protect is off
[    1.924101] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.924151] sd 0:0:0:0: [sda] Write cache: enabled, read cache:  enabled, doesn't support DPO or FUA
[    1.924449]  sda: sda1 sda2 <
[    1.944496] Freeing initrd memory: 7788k freed
[    1.969634]  sda5 >
[    1.970617] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.970689] sd 0:0:1:0: [sdb] 312581808 512-byte logical blocks: (160  GB/149 GiB)
[    1.970837] sd 0:0:1:0: [sdb] Write Protect is off
[    1.970843] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.970889] sd 0:0:1:0: [sdb] Write cache: enabled, read cache:  enabled, doesn't support DPO or FUA
[    1.971175]  sdb: sdb1 sdb2 < sdb5 sdb6 >
[    2.020122] sd 0:0:1:0: [sdb] Attached SCSI disk
[    2.060889] ata2.00: ATAPI: PHILIPS CDRW1610A, 0.010000, max UDMA/33
[    2.060933] ata2.01: ATAPI: PIONEER DVD-RW  DVR-107D, 1.18, max  UDMA/33
[    2.068424] ata2.00: configured for UDMA/33
[    2.076281] ata2.01: configured for UDMA/33
[    2.084828] scsi 1:0:0:0: CD-ROM            PHILIPS  CDRW1610A         02B0 PQ: 0 ANSI: 5
[    2.090770] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda  tray
[    2.090777] Uniform CD-ROM driver Revision: 3.20
[    2.091022] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.091175] sr 1:0:0:0: Attached scsi generic sg2 type 5
[    2.097394] scsi 1:0:1:0: CD-ROM            PIONEER  DVD-RW  DVR-107D  1.18 PQ: 0 ANSI: 5
[    2.115747] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda  tray
[    2.115923] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    2.116036] sr 1:0:1:0: Attached scsi generic sg3 type 5
[    2.116133] Freeing unused kernel memory: 656k freed
[    2.118134] Write protecting the kernel text: 4676k
[    2.118182] Write protecting the kernel read-only data: 1840k
[    2.164178] usb 5-1: new low speed USB device using uhci_hcd and  address 2
[    2.166775] udev: starting version 151
[    2.341848] usb 5-1: configuration #1 chosen from 1 choice
[    2.441111] usb 1-1.4: new high speed USB device using ehci_hcd and  address 4
[    2.534194] usb 1-1.4: configuration #1 chosen from 1 choice
[    2.534564] hub 1-1.4:1.0: USB hub found
[    2.535755] hub 1-1.4:1.0: 4 ports detected
[    2.639692] Floppy drive(s): fd0 is 1.44M
[    2.652643] usbcore: registered new interface driver hiddev
[    2.652840] usbcore: registered new interface driver usbhid
[    2.652855] usbhid: v2.6:USB HID core driver
[    2.662665] FDC 0 is a post-1991 82077
[    2.702720] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    2.702805] 8139cp 0000:00:0b.0: This (id 10ec:8139 rev 10) is not an  8139C+ compatible chip, use 8139too
[    2.729148] 8139too Fast Ethernet driver 0.9.28
[    2.729248] 8139too 0000:00:0b.0: PCI INT A -> Link[LNKB] ->  GSI 12 (level, low) -> IRQ 12
[    2.730693] eth0: RealTek RTL8139 at 0xcc00, 00:50:fc:4a:32:2e, IRQ  12
[    2.749231] input: USB Optical Mouse USB Optical Mouse as  /devices/pci0000:00/0000:00:09.1/usb5/5-1/5-1:1.0/input/input4
[    2.749843] a4tech 0003:09DA:0006.0001: input,hidraw0: USB HID v1.10  Mouse [USB Optical Mouse USB Optical Mouse] on usb-0000:00:09.1-1/input0
[    3.191763] EXT4-fs (sdb5): mounted filesystem with ordered data mode
[   13.147444] Adding 2245624k swap on /dev/sdb6.  Priority:-1 extents:1  across:2245624k 
[   13.234800] udev: starting version 151
[   13.416824] lp: driver loaded but no devices found
[   13.450244] sis630_smbus 0000:00:02.0: SIS630 comp. bus not detected,  module not inserted.
[   13.462535] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address:  0x0c00
[   13.462550] ACPI: resource 0000:00:02.1 [0xc00-0xc1f] conflicts with  ACPI region SMRG [0xc00-0xc1f]
[   13.462555] ACPI: If an ACPI driver is available for this device, you  should use it instead of the native driver
[   13.622022] shpchp: Standard Hot Plug PCI Controller Driver version:  0.4
[   13.643173] Linux agpgart interface v0.103
[   13.812587] agpgart-sis 0000:00:00.0: SiS chipset [1039/0735]
[   13.971114] agpgart-sis 0000:00:00.0: AGP aperture is 64M @  0xd0000000
[   14.236914] type=1505 audit(1275929215.237:2):   operation="profile_load" pid=443 name="/sbin/dhclient3"
[   14.237396] type=1505 audit(1275929215.237:3):   operation="profile_load" pid=443  name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.237673] type=1505 audit(1275929215.237:4):   operation="profile_load" pid=443  name="/usr/lib/connman/scripts/dhclient-script"
[   14.362988] cfg80211: Calling CRDA to update world regulatory domain
[   14.429977] parport_pc 00:09: reported by Plug and Play ACPI
[   14.430043] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   14.516521] lp0: using parport0 (interrupt-driven).
[   14.530563] cfg80211: World regulatory domain updated:
[   14.530574]     (start_freq - end_freq @ bandwidth),  (max_antenna_gain, max_eirp)
[   14.530579]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi,  2000 mBm)
[   14.530584]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi,  2000 mBm)
[   14.530588]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi,  2000 mBm)
[   14.530592]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi,  2000 mBm)
[   14.530597]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi,  2000 mBm)
[   14.774076] ppdev: user-space parallel port driver
[   14.775210] [drm] Initialized drm 1.1.0 20060810
[   14.907923] gameport: NS558 PnP Gameport is pnp00:0a/gameport0, io  0x201, speed 648kHz
[   15.021015] ath5k 0000:00:11.0: PCI INT A -> Link[LNKB] -> GSI  12 (level, low) -> IRQ 12
[   15.021130] ath5k 0000:00:11.0: registered as 'phy0'
[   15.846398] [drm] radeon defaulting to kernel modesetting.
[   15.846410] [drm] radeon kernel modesetting enabled.
[   15.846555] radeon 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI  5 (level, low) -> IRQ 5
[   15.902703] [drm] radeon: Initializing kernel modesetting.
[   15.911144] [drm] register mmio base: 0xCFEF0000
[   15.911153] [drm] register mmio size: 65536
[   15.911660] [drm] GPU reset succeed (RBBM_STATUS=0x00000140)
[   15.911686] [drm] Generation 2 PCI interface, using max accessible  memory
[   15.911703] agpgart-sis 0000:00:00.0: AGP 2.0 bridge
[   15.911744] agpgart-sis 0000:00:00.0: putting AGP V2 device into 4x  mode
[   15.911801] radeon 0000:01:00.0: putting AGP V2 device into 4x mode
[   15.911808] [drm] radeon: VRAM 128M
[   15.911811] [drm] radeon: VRAM from 0x00000000 to 0x07FFFFFF
[   15.911814] [drm] radeon: GTT 64M
[   15.911818] [drm] radeon: GTT from 0xD0000000 to 0xD3FFFFFF
[   15.911879] [drm] radeon: irq initialized.
[   15.912223] [drm] Detected VRAM RAM=128M, BAR=256M
[   15.912232] [drm] RAM width 64bits DDR
[   15.921540] [TTM] Zone  kernel: Available graphics memory: 383830  kiB.
[   15.921599] [drm] radeon: 128M of VRAM memory ready
[   15.921605] [drm] radeon: 64M of GTT memory ready.
[   15.921868] [drm] radeon: cp idle (0x02000603)
[   15.922126] [drm] Loading R200 Microcode
[   15.922995] platform radeon_cp.0: firmware: requesting  radeon/R200_cp.bin
[   16.185185] [drm] radeon: ring at 0x00000000D0000000
[   16.185214] [drm] ring test succeeded in 1 usecs
[   16.231082] type=1505 audit(1275929217.229:5):   operation="profile_load" pid=655  name="/usr/share/gdm/guest-session/Xsession"
[   16.242900] type=1505 audit(1275929217.241:6):   operation="profile_replace" pid=657 name="/sbin/dhclient3"
[   16.243436] type=1505 audit(1275929217.241:7):   operation="profile_replace" pid=657  name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   16.243731] type=1505 audit(1275929217.241:8):   operation="profile_replace" pid=657  name="/usr/lib/connman/scripts/dhclient-script"
[   16.398300] type=1505 audit(1275929217.397:9):   operation="profile_load" pid=660 name="/usr/bin/evince"
[   16.444308] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   16.446481] type=1505 audit(1275929217.445:10):   operation="profile_load" pid=660 name="/usr/bin/evince-previewer"
[   16.475848] [drm] radeon: ib pool ready.
[   16.476222] [drm] ib test succeeded in 0 usecs
[   16.478966] [drm] Default TV standard: PAL
[   16.478974] [drm] 27.000000000 MHz TV ref clk
[   16.478983] [drm] DFP table revision: 4
[   16.481415] [drm] Default TV standard: PAL
[   16.481423] [drm] 27.000000000 MHz TV ref clk
[   16.481712] [drm] Radeon Display Connectors
[   16.481716] [drm] Connector 0:
[   16.481719] [drm]   VGA
[   16.481725] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   16.481727] [drm]   Encoders:
[   16.481730] [drm]     CRT1: INTERNAL_DAC1
[   16.481733] [drm] Connector 1:
[   16.481735] [drm]   DVI-I
[   16.481738] [drm]   HPD1
[   16.481741] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   16.481744] [drm]   Encoders:
[   16.481747] [drm]     CRT2: INTERNAL_DAC2
[   16.481749] [drm]     DFP1: INTERNAL_TMDS1
[   16.481752] [drm] Connector 2:
[   16.481754] [drm]   S-video
[   16.481756] [drm]   Encoders:
[   16.481759] [drm]     TV1: INTERNAL_DAC2
[   16.483776] type=1505 audit(1275929217.481:11):   operation="profile_load" pid=660 name="/usr/bin/evince-thumbnailer"
[   17.049432] [drm] fb mappable at 0xB0040000
[   17.049439] [drm] vram apper at 0xB0000000
[   17.049442] [drm] size 5242880
[   17.049445] [drm] fb depth is 24
[   17.049447] [drm]    pitch is 5120
[   17.069169] fb0: radeondrmfb frame buffer device
[   17.069177] registered panic notifier
[   17.069194] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:00.0  on minor 0
[   17.085979] vga16fb: initializing
[   17.085996] vga16fb: mapped to 0xc00a0000
[   17.086009] vga16fb: not registering due to another framebuffer  present
[   17.305562] Console: switching to colour frame buffer device 160x64
[   17.954381] ath: EEPROM regdomain: 0x0
[   17.954390] ath: EEPROM indicates default country code should be used
[   17.954394] ath: doing EEPROM country->regdmn map search
[   17.954401] ath: country maps to regdmn code: 0x3a
[   17.954405] ath: Country alpha2 being used: US
[   17.954408] ath: Regpair used: 0x3a
[   18.015077] phy0: Selected rate control algorithm 'minstrel'
[   18.016487] ath5k phy0: Atheros AR2414 chip found (MAC: 0x79, PHY:  0x45)
[   18.018537] cfg80211: Calling CRDA for country: US
[   18.018739] Intel ICH 0000:00:02.7: PCI INT C -> Link[LNKC] ->  GSI 11 (level, low) -> IRQ 11
[   18.043919] cfg80211: Regulatory domain changed to country: US
[   18.043930]     (start_freq - end_freq @ bandwidth),  (max_antenna_gain, max_eirp)
[   18.043936]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi,  2700 mBm)
[   18.043940]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi,  1700 mBm)
[   18.043945]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi,  2000 mBm)
[   18.043949]     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi,  2000 mBm)
[   18.043953]     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi,  2000 mBm)
[   18.043957]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi,  3000 mBm)
[   18.216755] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.368269] intel8x0_measure_ac97_clock: measured 83563 usecs (4016  samples)
[   18.368278] intel8x0: clocking to 48000
[   22.074620] serial8250: too much work for irq11
[   22.188515] serial8250: too much work for irq11
[   22.303359] serial8250: too much work for irq11
[   22.417770] serial8250: too much work for irq11
[   22.532048] serial8250: too much work for irq11
[   22.646499] serial8250: too much work for irq11
[   22.760775] serial8250: too much work for irq11
[   22.874588] serial8250: too much work for irq11
[   22.989203] serial8250: too much work for irq11
[   23.102923] serial8250: too much work for irq11
[   23.220203] serial8250: too much work for irq11
[   23.334016] serial8250: too much work for irq11
[   23.637805] serial8250: too much work for irq11
[   23.751550] serial8250: too much work for irq11
[   23.867165] serial8250: too much work for irq11
[   23.980920] serial8250: too much work for irq11
[   24.094657] serial8250: too much work for irq11
[   24.238777] serial8250: too much work for irq11
[   24.352538] serial8250: too much work for irq11
[   24.466236] serial8250: too much work for irq11
[   24.579997] serial8250: too much work for irq11
[   24.719799] serial8250: too much work for irq11
[   24.835392] serial8250: too much work for irq11
[   24.950846] serial8250: too much work for irq11
[   25.065147] serial8250: too much work for irq11
[   25.181526] serial8250: too much work for irq11
[   25.295724] serial8250: too much work for irq11
[   25.412108] serial8250: too much work for irq11
[   25.526312] serial8250: too much work for irq11
[   25.729417] serial8250: too much work for irq11
[   25.842796] serial8250: too much work for irq11
[   25.964970] serial8250: too much work for irq11
[   26.079887] serial8250: too much work for irq11
[   26.196854] serial8250: too much work for irq11
[   26.312892] serial8250: too much work for irq11
[   26.428844] serial8250: too much work for irq11
[   26.543642] serial8250: too much work for irq11
[   26.696167] serial8250: too much work for irq11
[   26.867142] serial8250: too much work for irq11
[   27.034853] serial8250: too much work for irq11
[   27.034944] eth0: no IPv6 routers present
[   27.208535] serial8250: too much work for irq11
[   27.379296] serial8250: too much work for irq11
[   27.549910] serial8250: too much work for irq11
[   27.719665] serial8250: too much work for irq11
[   27.891292] serial8250: too much work for irq11
[   28.062049] serial8250: too much work for irq11
[   28.232760] serial8250: too much work for irq11
[   28.401983] serial8250: too much work for irq11
[   28.571921] serial8250: too much work for irq11
[   28.744720] serial8250: too much work for irq11
[   28.913143] serial8250: too much work for irq11
[   29.086087] serial8250: too much work for irq11
[   29.254750] serial8250: too much work for irq11
[   29.427201] serial8250: too much work for irq11
[   29.596741] serial8250: too much work for irq11
[   29.767511] serial8250: too much work for irq11
[   29.931477] serial8250: too much work for irq11
[   30.046326] serial8250: too much work for irq11
[   30.162884] serial8250: too much work for irq11
[   30.277632] serial8250: too much work for irq11
[   30.450815] serial8250: too much work for irq11
[   30.620878] serial8250: too much work for irq11
[   30.792184] serial8250: too much work for irq11
[   30.962250] serial8250: too much work for irq11
[   31.131897] serial8250: too much work for irq11
[   31.304135] serial8250: too much work for irq11
[   31.473842] serial8250: too much work for irq11
[   31.644113] serial8250: too much work for irq11
[   31.873043] serial8250: too much work for irq11
[   32.043469] serial8250: too much work for irq11
[   32.213872] serial8250: too much work for irq11
[   32.385082] serial8250: too much work for irq11
[   32.555574] serial8250: too much work for irq11
[   32.726230] serial8250: too much work for irq11
[   32.929062] serial8250: too much work for irq11
[   33.042818] serial8250: too much work for irq11
[   48.557543] serial8250: too much work for irq11
[   48.731787] serial8250: too much work for irq11
[   48.902670] serial8250: too much work for irq11
[   49.038194] serial8250: too much work for irq11
[   49.208864] serial8250: too much work for irq11
[   49.379470] serial8250: too much work for irq11
[   49.550029] serial8250: too much work for irq11
[   49.720708] serial8250: too much work for irq11
[   49.891321] serial8250: too much work for irq11
[   50.061982] serial8250: too much work for irq11
[   50.232559] serial8250: too much work for irq11
[   50.403184] serial8250: too much work for irq11
[   50.573853] serial8250: too much work for irq11
[   50.744499] serial8250: too much work for irq11
[   50.915046] serial8250: too much work for irq11
[   51.085736] serial8250: too much work for irq11
[   51.256314] serial8250: too much work for irq11
[   51.426946] serial8250: too much work for irq11
[   51.597526] serial8250: too much work for irq11
[   51.768234] serial8250: too much work for irq11
[   51.938782] serial8250: too much work for irq11
[   52.109531] serial8250: too much work for irq11
[   52.280061] serial8250: too much work for irq11
[   52.450671] serial8250: too much work for irq11
[   52.621296] serial8250: too much work for irq11
[   52.791985] serial8250: too much work for irq11
[   52.962512] serial8250: too much work for irq11
[   53.133274] serial8250: too much work for irq11
[   53.303772] serial8250: too much work for irq11
[   53.474437] serial8250: too much work for irq11
[   53.645080] serial8250: too much work for irq11
[   53.815647] serial8250: too much work for irq11
[   53.986243] serial8250: too much work for irq11
[   54.157069] serial8250: too much work for irq11
[   54.176055] end_request: I/O error, dev fd0, sector 0
[   54.327530] serial8250: too much work for irq11
[   54.327598] end_request: I/O error, dev fd0, sector 0
[   54.533263] serial8250: too much work for irq11
[   54.703838] serial8250: too much work for irq11
[   54.874472] serial8250: too much work for irq11
[   55.045187] serial8250: too much work for irq11
[   55.215933] serial8250: too much work for irq11
[   55.386320] serial8250: too much work for irq11
[   55.556984] serial8250: too much work for irq11
[   55.727639] serial8250: too much work for irq11
[   55.898227] serial8250: too much work for irq11
[   56.068938] serial8250: too much work for irq11
[   56.239482] serial8250: too much work for irq11
[   56.410082] serial8250: too much work for irq11
[   56.580780] serial8250: too much work for irq11
[   56.751358] serial8250: too much work for irq11
[   56.922018] serial8250: too much work for irq11
[   57.092608] serial8250: too much work for irq11
[   57.263226] serial8250: too much work for irq11
[   57.433873] serial8250: too much work for irq11
[   57.604438] serial8250: too much work for irq11
[   57.775136] serial8250: too much work for irq11
[   57.945749] serial8250: too much work for irq11
[   58.116388] serial8250: too much work for irq11
[   58.286944] serial8250: too much work for irq11
[   58.457643] serial8250: too much work for irq11
[   58.628197] serial8250: too much work for irq11
[   58.798875] serial8250: too much work for irq11
[   58.969550] serial8250: too much work for irq11
[   59.140204] serial8250: too much work for irq11
[   59.310715] serial8250: too much work for irq11
[   59.481417] serial8250: too much work for irq11
[   59.651995] serial8250: too much work for irq11
[   59.822614] serial8250: too much work for irq11
[   59.993272] serial8250: too much work for irq11
[   60.163877] serial8250: too much work for irq11
[   60.334479] serial8250: too much work for irq11
[   60.505169] serial8250: too much work for irq11
[   60.675741] serial8250: too much work for irq11
[   60.846315] serial8250: too much work for irq11
[   61.017030] serial8250: too much work for irq11
[   61.187577] serial8250: too much work for irq11
[   61.358249] serial8250: too much work for irq11
[   61.528887] serial8250: too much work for irq11
[   61.699463] serial8250: too much work for irq11
[   61.870079] serial8250: too much work for irq11
[   62.040745] serial8250: too much work for irq11
[   62.211316] serial8250: too much work for irq11
[   62.382028] serial8250: too much work for irq11
[   62.552625] serial8250: too much work for irq11
[   62.723223] serial8250: too much work for irq11
[   62.893839] serial8250: too much work for irq11
[   63.064505] serial8250: too much work for irq11
[   63.235087] serial8250: too much work for irq11
[   63.405740] serial8250: too much work for irq11
[   63.576355] serial8250: too much work for irq11
[   63.746901] serial8250: too much work for irq11
borderfox@borderfox-desktop:~$ 

```

---

### Post by borderfox on 2010-06-07
I managed to turn ACPI off in the BIOS - but this just gives me an unbootable machine with a continuous error:  ***serial8250: too much work for irq11***

proc/irq/11 contains these empty folders; 
ehci_hcd:usb1
ohci_hcd:usb2
SiS S17012

Anyone any ideas?

---

### Post by borderfox on 2010-06-08
It seems teh serial8250 error is not affecting the installation of the cardreader as I have managed to do that now.  As I've spent much time in researching this error but failed to find much direct info on it - or at least info leading to a solution - I am going to leave it be.  It doesn't appear to be preventing my use of any services on the machine as it stands right now so I will leave it as is.
 
I do have one last issue with the cardreader install but I will post that seperately.

---

