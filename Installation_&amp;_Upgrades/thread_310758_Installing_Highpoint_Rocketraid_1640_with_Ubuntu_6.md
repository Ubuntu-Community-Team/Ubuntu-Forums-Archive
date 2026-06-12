---
title: "Installing Highpoint Rocketraid 1640 with Ubuntu 6.10"
date: 2006-12-01
forum: Installation &amp; Upgrades
---

### Post by UBUn00b3 on 2006-12-01
I am quite new to Ubuntu and am trying to build up the box that will act as my transition platform from Windows to Linux.

I am booting from an IDE drive with no issues. I have a RocketRaid 1640 card with 4 SATA drives that I am trying to bring online as a RAID 5 array for data storage.

The highpoint driver [http://www.highpoint-tech.com/USA/bios_rr1640.htm]("http://www.highpoint-tech.com/USA/bios_rr1640.htm")
requires that it be compiled. Having read the various postings and guides in the forum and having no luck I thought I would put out a bleg for step-by-step (idiot resistant) instructions.

When I 'make' the file I get the following:
entry.c:438: error: dereferencing pointer to incomplete type
entry.c:438: error: ‘DID_OK’ undeclared (first use in this function)
entry.c:444: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:446: error: dereferencing pointer to incomplete type
entry.c:446: error: ‘DRIVER_INVALID’ undeclared (first use in this function)
entry.c:446: error: ‘SUGGEST_ABORT’ undeclared (first use in this function)
entry.c:446: error: ‘DID_ABORT’ undeclared (first use in this function)
entry.c:449: warning: incompatible implicit declaration of built-in function ‘memset’
entry.c:452: error: dereferencing pointer to incomplete type
entry.c:460: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:462: error: dereferencing pointer to incomplete type
entry.c:467: error: ‘u8’ undeclared (first use in this function)
entry.c:470: error: expected ‘;’ before ‘cap’
entry.c:476: error: dereferencing pointer to incomplete type
entry.c:490: error: dereferencing pointer to incomplete type
entry.c:494: error: dereferencing pointer to incomplete type
entry.c:494: error: dereferencing pointer to incomplete type
entry.c:494: error: dereferencing pointer to incomplete type
entry.c:495: error: dereferencing pointer to incomplete type
entry.c:498: error: dereferencing pointer to incomplete type
entry.c:498: error: dereferencing pointer to incomplete type
entry.c:499: error: dereferencing pointer to incomplete type
entry.c:499: error: dereferencing pointer to incomplete type
entry.c:500: error: dereferencing pointer to incomplete type
entry.c:500: error: dereferencing pointer to incomplete type
entry.c:503: error: dereferencing pointer to incomplete type
entry.c:524: error: dereferencing pointer to incomplete type
entry.c:530: error: dereferencing pointer to incomplete type
entry.c:539: error: dereferencing pointer to incomplete type
entry.c: In function ‘hpt3xx_QueueCommand’:
entry.c:566: error: dereferencing pointer to incomplete type
entry.c:567: error: dereferencing pointer to incomplete type
entry.c:567: error: ‘DID_OK’ undeclared (first use in this function)
entry.c:572: error: dereferencing pointer to incomplete type
entry.c:578: warning: implicit declaration of function ‘spin_lock_irqsave’
entry.c:578: error: ‘driver_lock’ undeclared (first use in this function)
entry.c:580: error: dereferencing pointer to incomplete type
entry.c:580: error: dereferencing pointer to incomplete type
entry.c:580: error: dereferencing pointer to incomplete type
entry.c:583: error: dereferencing pointer to incomplete type
entry.c:583: error: dereferencing pointer to incomplete type
entry.c:585: error: dereferencing pointer to incomplete type
entry.c:585: error: ‘DID_BAD_TARGET’ undeclared (first use in this function)
entry.c:586: error: dereferencing pointer to incomplete type
entry.c:589: error: dereferencing pointer to incomplete type
entry.c:589: error: ‘DPC_Request_Nums’ undeclared (first use in this function)
entry.c:593: error: dereferencing pointer to incomplete type
entry.c:599: warning: implicit declaration of function ‘spin_unlock_irqrestore’
entry.c: In function ‘internal_done’:
entry.c:612: error: dereferencing pointer to incomplete type
entry.c: In function ‘hpt3xx_Command’:
entry.c:625: error: dereferencing pointer to incomplete type
entry.c:628: error: ‘jiffies’ undeclared (first use in this function)
entry.c:628: error: ‘HZ’ undeclared (first use in this function)
entry.c:629: error: dereferencing pointer to incomplete type
entry.c:629: warning: implicit declaration of function ‘time_before’
entry.c:629: warning: implicit declaration of function ‘schedule’
entry.c:631: error: dereferencing pointer to incomplete type
entry.c:631: error: dereferencing pointer to incomplete type
entry.c:631: error: ‘DID_ERROR’ undeclared (first use in this function)
entry.c:632: error: dereferencing pointer to incomplete type
entry.c: In function ‘launch_worker_thread’:
entry.c:638: warning: implicit declaration of function ‘kernel_thread’
entry.c:639: warning: implicit declaration of function ‘down’
entry.c: In function ‘hpt3xx_Detect’:
entry.c:671: warning: implicit declaration of function ‘kmalloc’
entry.c:671: error: ‘GFP_ATOMIC’ undeclared (first use in this function)
entry.c:671: warning: assignment makes pointer from integer without a cast
entry.c:687: warning: initialization makes pointer from integer without a cast
entry.c:687: warning: incompatible implicit declaration of built-in function ‘memset’
entry.c:690: warning: implicit declaration of function ‘kfree’
entry.c:711: warning: implicit declaration of function ‘scsi_register’
entry.c:711: warning: assignment makes pointer from integer without a cast
entry.c:712: error: dereferencing pointer to incomplete type
entry.c:713: error: dereferencing pointer to incomplete type
entry.c:714: error: dereferencing pointer to incomplete type
entry.c:715: error: dereferencing pointer to incomplete type
entry.c:716: error: dereferencing pointer to incomplete type
entry.c:718: error: dereferencing pointer to incomplete type
entry.c:719: error: dereferencing pointer to incomplete type
entry.c:720: error: dereferencing pointer to incomplete type
entry.c:721: error: dereferencing pointer to incomplete type
entry.c:728: warning: implicit declaration of function ‘pci_find_device’
entry.c:728: warning: assignment makes pointer from integer without a cast
entry.c:731: error: dereferencing pointer to incomplete type
entry.c:732: error: dereferencing pointer to incomplete type
entry.c:735: warning: implicit declaration of function ‘pci_enable_device’
entry.c:741: error: dereferencing pointer to incomplete type
entry.c:741: error: dereferencing pointer to incomplete type
entry.c:742: error: dereferencing pointer to incomplete type
entry.c:743: warning: implicit declaration of function ‘pci_set_master’
entry.c:746: warning: implicit declaration of function ‘pci_set_dma_mask’
entry.c:763: warning: incompatible implicit declaration of built-in function ‘memset’
entry.c:767: error: dereferencing pointer to incomplete type
entry.c:772: warning: implicit declaration of function ‘request_irq’
entry.c:772: error: ‘Irq_Handler’ undeclared (first use in this function)
entry.c:772: error: ‘SA_SHIRQ’ undeclared (first use in this function)
entry.c:773: error: ‘SA_INTERRUPT’ undeclared (first use in this function)
entry.c:781: warning: implicit declaration of function ‘init_timer’
entry.c:803: warning: implicit declaration of function ‘register_reboot_notifier’
entry.c: In function ‘hpt3xx_Reset’:
entry.c:837: error: ‘KERN_WARNING’ undeclared (first use in this function)
entry.c:837: error: expected ‘)’ before string constant
entry.c:839: error: ‘FAILED’ undeclared (first use in this function)
entry.c:842: error: dereferencing pointer to incomplete type
entry.c:842: error: dereferencing pointer to incomplete type
entry.c:842: error: dereferencing pointer to incomplete type
entry.c:842: error: dereferencing pointer to incomplete type
entry.c:848: error: dereferencing pointer to incomplete type
entry.c:853: error: ‘driver_lock’ undeclared (first use in this function)
entry.c:855: error: dereferencing pointer to incomplete type
entry.c:864: error: dereferencing pointer to incomplete type
entry.c:866: error: dereferencing pointer to incomplete type
entry.c:867: error: dereferencing pointer to incomplete type
entry.c:868: error: dereferencing pointer to incomplete type
entry.c:868: error: ‘DID_RESET’ undeclared (first use in this function)
entry.c:869: error: dereferencing pointer to incomplete type
entry.c:877: error: dereferencing pointer to incomplete type
entry.c:880: error: ‘SUCCESS’ undeclared (first use in this function)
entry.c: In function ‘hpt3xx_cleanup’:
entry.c:905: error: ‘driver_lock’ undeclared (first use in this function)
entry.c:915: warning: implicit declaration of function ‘del_timer’
entry.c:929: warning: implicit declaration of function ‘free_irq’
entry.c: In function ‘hpt3xx_Release’:
entry.c:942: warning: implicit declaration of function ‘unregister_reboot_notifier’
entry.c:943: warning: implicit declaration of function ‘scsi_unregister’
entry.c: At top level:
entry.c:987: error: expected declaration specifiers or ‘...’ before ‘ulong’
entry.c:988: error: conflicting types for ‘hpt_halt’
entry.c:120: error: previous declaration of ‘hpt_halt’ was here
entry.c: In function ‘hpt_halt’:
entry.c:989: error: ‘event’ undeclared (first use in this function)
entry.c:989: error: ‘SYS_RESTART’ undeclared (first use in this function)
entry.c:989: error: ‘SYS_HALT’ undeclared (first use in this function)
entry.c:989: error: ‘SYS_POWER_OFF’ undeclared (first use in this function)
entry.c:990: error: ‘NOTIFY_DONE’ undeclared (first use in this function)
entry.c:994: error: ‘NOTIFY_OK’ undeclared (first use in this function)
entry.c: In function ‘fOsBuildSgl’:
entry.c:1002: error: dereferencing pointer to incomplete type
entry.c:1005: error: dereferencing pointer to incomplete type
entry.c:1031: error: dereferencing pointer to incomplete type
entry.c:1033: warning: implicit declaration of function ‘page_address’
entry.c:1033: error: invalid use of undefined type ‘struct scatterlist’
entry.c:1033: error: dereferencing pointer to incomplete type
entry.c:1033: error: invalid use of undefined type ‘struct scatterlist’
entry.c:1033: error: dereferencing pointer to incomplete type
entry.c:1041: error: invalid use of undefined type ‘struct scatterlist’
entry.c:1041: error: dereferencing pointer to incomplete type
entry.c:1042: error: dereferencing pointer to incomplete type
entry.c:1047: error: dereferencing pointer to incomplete type
entry.c:1048: error: dereferencing pointer to incomplete type
entry.c:1053: error: dereferencing pointer to incomplete type
entry.c:1054: error: dereferencing pointer to incomplete type
entry.c:1055: error: dereferencing pointer to incomplete type
entry.c:1055: warning: implicit declaration of function ‘pci_map_sg’
entry.c:1055: error: dereferencing pointer to incomplete type
entry.c:1056: error: dereferencing pointer to incomplete type
entry.c:1056: error: dereferencing pointer to incomplete type
entry.c:1058: error: dereferencing pointer to incomplete type
entry.c:1060: error: dereferencing pointer to incomplete type
entry.c:1061: warning: implicit declaration of function ‘sg_dma_address’
entry.c:1061: error: invalid use of undefined type ‘struct scatterlist’
entry.c:1061: error: dereferencing pointer to incomplete type
entry.c:1063: warning: implicit declaration of function ‘sg_dma_len’
entry.c:1063: error: invalid use of undefined type ‘struct scatterlist’
entry.c:1063: error: dereferencing pointer to incomplete type
entry.c:1065: error: dereferencing pointer to incomplete type
entry.c:1069: error: dereferencing pointer to incomplete type
entry.c:1070: error: dereferencing pointer to incomplete type
entry.c:1070: warning: implicit declaration of function ‘pci_map_single’
entry.c:1070: error: dereferencing pointer to incomplete type
entry.c:1070: error: dereferencing pointer to incomplete type
entry.c:1071: error: dereferencing pointer to incomplete type
entry.c:1071: error: dereferencing pointer to incomplete type
entry.c:1072: error: dereferencing pointer to incomplete type
entry.c:1074: error: dereferencing pointer to incomplete type
entry.c:1076: error: dereferencing pointer to incomplete type
entry.c: In function ‘fOsCommandDone’:
entry.c:1088: error: dereferencing pointer to incomplete type
entry.c:1089: error: dereferencing pointer to incomplete type
entry.c:1090: warning: implicit declaration of function ‘pci_unmap_sg’
entry.c:1091: error: dereferencing pointer to incomplete type
entry.c:1092: error: dereferencing pointer to incomplete type
entry.c:1093: error: dereferencing pointer to incomplete type
entry.c:1094: error: dereferencing pointer to incomplete type
entry.c:1097: warning: implicit declaration of function ‘pci_unmap_single’
entry.c:1098: error: dereferencing pointer to incomplete type
entry.c:1099: error: dereferencing pointer to incomplete type
entry.c:1100: error: dereferencing pointer to incomplete type
entry.c:1101: error: dereferencing pointer to incomplete type
entry.c:1108: error: dereferencing pointer to incomplete type
entry.c:1108: error: ‘DID_OK’ undeclared (first use in this function)
entry.c:1112: error: dereferencing pointer to incomplete type
entry.c:1112: error: ‘DID_BAD_TARGET’ undeclared (first use in this function)
entry.c:1116: error: dereferencing pointer to incomplete type
entry.c:1116: error: ‘DID_BUS_BUSY’ undeclared (first use in this function)
entry.c:1120: error: dereferencing pointer to incomplete type
entry.c:1120: error: ‘DID_NO_CONNECT’ undeclared (first use in this function)
entry.c:1124: error: dereferencing pointer to incomplete type
entry.c:1124: error: ‘DID_RESET’ undeclared (first use in this function)
entry.c:1128: error: dereferencing pointer to incomplete type
entry.c:1128: error: ‘DRIVER_INVALID’ undeclared (first use in this function)
entry.c:1128: error: ‘SUGGEST_ABORT’ undeclared (first use in this function)
entry.c:1128: error: ‘DID_ABORT’ undeclared (first use in this function)
entry.c: In function ‘OsSetDeviceTable’:
entry.c:1151: warning: incompatible implicit declaration of built-in function ‘memcpy’
entry.c: In function ‘SetInquiryData’:
entry.c:1169: warning: implicit declaration of function ‘cpu_to_le16’
entry.c:1188: warning: incompatible implicit declaration of built-in function ‘memcpy’
entry.c: In function ‘hpt_worker_thread’:
entry.c:1226: error: variable ‘semQueue’ has initializer but incomplete type
entry.c:1226: error: storage size of ‘semQueue’ isn’t known
entry.c:1227: error: variable ‘sem’ has initializer but incomplete type
entry.c:1227: error: storage size of ‘sem’ isn’t known
entry.c:1229: warning: implicit declaration of function ‘lock_kernel’
entry.c:1235: warning: implicit declaration of function ‘daemonize’
entry.c:1262: warning: implicit declaration of function ‘sprintf’
entry.c:1262: warning: incompatible implicit declaration of built-in function ‘sprintf’
entry.c:1262: error: ‘current’ undeclared (first use in this function)
entry.c:1268: warning: implicit declaration of function ‘unlock_kernel’
entry.c:1276: warning: implicit declaration of function ‘down_interruptible’
entry.c:1281: error: dereferencing pointer to incomplete type
entry.c:1285: error: ‘DpcQueueLock’ undeclared (first use in this function)
entry.c:1289: warning: implicit declaration of function ‘atomic_inc’
entry.c:1289: error: ‘DPC_Request_Nums’ undeclared (first use in this function)
entry.c:1295: warning: implicit declaration of function ‘atomic_dec_and_test’
entry.c:1296: error: ‘driver_lock’ undeclared (first use in this function)
entry.c:1297: error: dereferencing pointer to incomplete type
entry.c:1313: warning: implicit declaration of function ‘signal_pending’
entry.c:1227: warning: unused variable ‘sem’
entry.c:1226: warning: unused variable ‘semQueue’
entry.c: In function ‘hpt_queue_dpc’:
entry.c:1347: error: ‘DpcQueueLock’ undeclared (first use in this function)
entry.c: At top level:
entry.c:1367: error: variable ‘driver_template’ has initializer but incomplete type
entry.c:1368: error: unknown field ‘name’ specified in initializer
entry.c:1368: warning: excess elements in struct initializer
entry.c:1368: warning: (near initialization for ‘driver_template’)
entry.c:1369: error: unknown field ‘detect’ specified in initializer
entry.c:1369: warning: excess elements in struct initializer
entry.c:1369: warning: (near initialization for ‘driver_template’)
entry.c:1370: error: unknown field ‘release’ specified in initializer
entry.c:1370: warning: excess elements in struct initializer
entry.c:1370: warning: (near initialization for ‘driver_template’)
entry.c:1371: error: unknown field ‘queuecommand’ specified in initializer
entry.c:1371: warning: excess elements in struct initializer
entry.c:1371: warning: (near initialization for ‘driver_template’)
entry.c:1372: error: unknown field ‘eh_device_reset_handler’ specified in initializer
entry.c:1372: warning: excess elements in struct initializer
entry.c:1372: warning: (near initialization for ‘driver_template’)
entry.c:1373: error: unknown field ‘eh_bus_reset_handler’ specified in initializer
entry.c:1373: warning: excess elements in struct initializer
entry.c:1373: warning: (near initialization for ‘driver_template’)
entry.c:1374: error: unknown field ‘can_queue’ specified in initializer
entry.c:1374: warning: excess elements in struct initializer
entry.c:1374: warning: (near initialization for ‘driver_template’)
entry.c:1375: error: unknown field ‘sg_tablesize’ specified in initializer
entry.c:1375: warning: excess elements in struct initializer
entry.c:1375: warning: (near initialization for ‘driver_template’)
entry.c:1377: error: unknown field ‘cmd_per_lun’ specified in initializer
entry.c:1377: warning: excess elements in struct initializer
entry.c:1377: warning: (near initialization for ‘driver_template’)
entry.c:1378: error: unknown field ‘unchecked_isa_dma’ specified in initializer
entry.c:1378: warning: excess elements in struct initializer
entry.c:1378: warning: (near initialization for ‘driver_template’)
entry.c:1379: error: unknown field ‘emulated’ specified in initializer
entry.c:1379: warning: excess elements in struct initializer
entry.c:1379: warning: (near initialization for ‘driver_template’)
entry.c:1396: error: unknown field ‘proc_name’ specified in initializer
entry.c:1396: warning: excess elements in struct initializer
entry.c:1396: warning: (near initialization for ‘driver_template’)
entry.c:1397: error: unknown field ‘proc_info’ specified in initializer
entry.c:1397: warning: excess elements in struct initializer
entry.c:1397: warning: (near initialization for ‘driver_template’)
entry.c:1398: error: unknown field ‘max_sectors’ specified in initializer
entry.c:1398: warning: excess elements in struct initializer
entry.c:1398: warning: (near initialization for ‘driver_template’)
entry.c:1399: error: unknown field ‘use_clustering’ specified in initializer
entry.c:1399: error: ‘DISABLE_CLUSTERING’ undeclared here (not in a function)
entry.c:1399: warning: excess elements in struct initializer
entry.c:1399: warning: (near initialization for ‘driver_template’)
entry.c:1401: error: unknown field ‘this_id’ specified in initializer
entry.c:1402: warning: excess elements in struct initializer
entry.c:1402: warning: (near initialization for ‘driver_template’)
entry.c:1444: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘init_this_scsi_driver’
entry.c:1479: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘exit_this_scsi_driver’
entry.c:1499: warning: data definition has no type or storage class
entry.c:1499: warning: type defaults to ‘int’ in declaration of ‘module_init’
entry.c:1499: warning: parameter names (without types) in function declaration
entry.c:1500: warning: data definition has no type or storage class
entry.c:1500: warning: type defaults to ‘int’ in declaration of ‘module_exit’
entry.c:1500: warning: parameter names (without types) in function declaration
entry.c: In function ‘pcicfg_read_byte’:
entry.c:1505: warning: implicit declaration of function ‘pci_find_slot’
entry.c:1505: warning: initialization makes pointer from integer without a cast
entry.c:1508: warning: implicit declaration of function ‘pci_read_config_byte’
entry.c: In function ‘pcicfg_read_word’:
entry.c:1514: warning: initialization makes pointer from integer without a cast
entry.c:1517: warning: implicit declaration of function ‘pci_read_config_word’
entry.c: In function ‘pcicfg_read_dword’:
entry.c:1523: warning: initialization makes pointer from integer without a cast
entry.c:1526: warning: implicit declaration of function ‘pci_read_config_dword’
entry.c: In function ‘pcicfg_write_byte’:
entry.c:1532: warning: initialization makes pointer from integer without a cast
entry.c:1535: warning: implicit declaration of function ‘pci_write_config_byte’
entry.c: In function ‘pcicfg_write_word’:
entry.c:1539: warning: initialization makes pointer from integer without a cast
entry.c:1542: warning: implicit declaration of function ‘pci_write_config_word’
entry.c: In function ‘pcicfg_write_dword’:
entry.c:1546: warning: initialization makes pointer from integer without a cast
entry.c:1549: warning: implicit declaration of function ‘pci_write_config_dword’
entry.c: At top level:
entry.c:1554: error: expected declaration specifiers or ‘...’ before string constant
entry.c:1554: warning: data definition has no type or storage class
entry.c:1554: warning: type defaults to ‘int’ in declaration of ‘MODULE_LICENSE’
entry.c:1554: warning: function declaration isn’t a prototype
entry.c: In function ‘StallExec’:
entry.c:1570: error: ‘MAX_UDELAY_MS’ undeclared (first use in this function)
entry.c:1570: warning: implicit declaration of function ‘udelay’
entry.c:1570: warning: implicit declaration of function ‘mdelay’
entry.c: In function ‘fOsPhysicalAddress’:
entry.c:1575: warning: implicit declaration of function ‘virt_to_bus’
entry.c: In function ‘os_alloc_page’:
entry.c:1576: error: ‘GFP_ATOMIC’ undeclared (first use in this function)
entry.c:1576: warning: return makes pointer from integer without a cast
entry.c: In function ‘os_alloc_dma_page’:
entry.c:1577: error: ‘GFP_ATOMIC’ undeclared (first use in this function)
entry.c:1577: warning: return makes pointer from integer without a cast
entry.c: In function ‘os_printk’:
entry.c:1621: error: ‘va_list’ undeclared (first use in this function)
entry.c:1621: error: expected ‘;’ before ‘ap’
entry.c:1623: warning: implicit declaration of function ‘va_start’
entry.c:1623: error: ‘ap’ undeclared (first use in this function)
entry.c:1624: warning: implicit declaration of function ‘vsprintf’
entry.c:1625: warning: implicit declaration of function ‘va_end’
entry.c: In function ‘os_memcmp’:
entry.c:1629: warning: implicit declaration of function ‘memcmp’
entry.c: In function ‘os_memcpy’:
entry.c:1630: warning: incompatible implicit declaration of built-in function ‘memcpy’
entry.c: In function ‘os_memset’:
entry.c:1631: warning: incompatible implicit declaration of built-in function ‘memset’
entry.c: In function ‘os_strlen’:
entry.c:1632: warning: implicit declaration of function ‘strlen’
entry.c:1632: warning: incompatible implicit declaration of built-in function ‘strlen’
entry.c: In function ‘CPU_TO_LE32’:
entry.c:1635: warning: implicit declaration of function ‘cpu_to_le32’
entry.c: In function ‘LE16_TO_CPU’:
entry.c:1636: warning: implicit declaration of function ‘le16_to_cpu’
entry.c: In function ‘LE32_TO_CPU’:
entry.c:1637: warning: implicit declaration of function ‘le32_to_cpu’
entry.c: In function ‘CPU_TO_BE16’:
entry.c:1638: warning: implicit declaration of function ‘cpu_to_be16’
entry.c: In function ‘CPU_TO_BE32’:
entry.c:1639: warning: implicit declaration of function ‘cpu_to_be32’
entry.c: In function ‘BE16_TO_CPU’:
entry.c:1640: warning: implicit declaration of function ‘be16_to_cpu’
entry.c: In function ‘BE32_TO_CPU’:
entry.c:1641: warning: implicit declaration of function ‘be32_to_cpu’
In file included from hpt.c:162:
hptproc.c: In function ‘hpt_set_asc_info’:
hptproc.c:47: warning: implicit declaration of function ‘strncmp’
hptproc.c:52: error: ‘driver_lock’ undeclared (first use in this function)
hptproc.c:98: warning: passing argument 1 of ‘sd_inuse’ from incompatible pointer type
hptproc.c: In function ‘hpt_set_info’:
hptproc.c:250: warning: implicit declaration of function ‘access_ok’
hptproc.c:250: error: ‘VERIFY_READ’ undeclared (first use in this function)
hptproc.c:256: error: ‘VERIFY_WRITE’ undeclared (first use in this function)
hptproc.c:275: error: ‘GFP_ATOMIC’ undeclared (first use in this function)
hptproc.c:275: warning: assignment makes pointer from integer without a cast
hptproc.c:281: warning: implicit declaration of function ‘copy_from_user’
hptproc.c:295: warning: implicit declaration of function ‘copy_to_user’
hptproc.c: In function ‘hpt_copy_mem_info’:
hptproc.c:352: warning: incompatible implicit declaration of built-in function ‘memcpy’
hptproc.c: In function ‘hpt_copy_info’:
hptproc.c:368: error: ‘va_list’ undeclared (first use in this function)
hptproc.c:368: error: expected ‘;’ before ‘args’
hptproc.c:372: error: ‘args’ undeclared (first use in this function)
hptproc.c: In function ‘hpt_copy_disk_info’:
hptproc.c:387: warning: incompatible implicit declaration of built-in function ‘memcpy’
hptproc.c: In function ‘hpt_copy_array_info’:
hptproc.c:459: warning: incompatible implicit declaration of built-in function ‘sprintf’
hptproc.c:463: warning: incompatible implicit declaration of built-in function ‘sprintf’
hptproc.c: In function ‘get_sd_name’:
hptproc.c:501: warning: passing argument 1 of ‘get_bdev’ from incompatible pointer type
hptproc.c:504: warning: incompatible implicit declaration of built-in function ‘sprintf’
hptproc.c:504: error: dereferencing pointer to incomplete type
hptproc.c: At top level:
hptproc.c:510: error: expected declaration specifiers or ‘...’ before ‘off_t’
hptproc.c: In function ‘hpt_get_info’:
hptproc.c:520: error: ‘offset’ undeclared (first use in this function)
hptproc.c:558: warning: incompatible implicit declaration of built-in function ‘memset’
hptproc.c: At top level:
hptproc.c:604: error: expected declaration specifiers or ‘...’ before ‘off_t’
hptproc.c: In function ‘hpt3xx_ProcInfo’:
hptproc.c:613: error: ‘offset’ undeclared (first use in this function)
hptproc.c:613: error: too many arguments to function ‘hpt_get_info’
hptproc.c: At top level:
hptproc.c:618: error: expected declaration specifiers or ‘...’ before ‘off_t’
hptproc.c: In function ‘hpt3xx_ProcInfo26’:
hptproc.c:620: error: ‘offset’ undeclared (first use in this function)
hptproc.c:620: error: dereferencing pointer to incomplete type
hptproc.c:620: error: too many arguments to function ‘hpt3xx_ProcInfo’
In file included from ioctl.c:6,
                 from hpt.c:163:
gui_lib.c: In function ‘get_array_info’:
gui_lib.c:119: warning: incompatible implicit declaration of built-in function ‘memcpy’
gui_lib.c: In function ‘get_disk_info’:
gui_lib.c:329: warning: incompatible implicit declaration of built-in function ‘memcpy’
gui_lib.c: In function ‘hpt_get_driver_capabilities’:
gui_lib.c:338: warning: incompatible implicit declaration of built-in function ‘memset’
gui_lib.c: In function ‘hpt_get_controller_info’:
gui_lib.c:408: warning: implicit declaration of function ‘strcpy’
gui_lib.c:408: warning: incompatible implicit declaration of built-in function ‘strcpy’
gui_lib.c:408: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness
gui_lib.c:414: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness
gui_lib.c: In function ‘hpt_create_array’:
gui_lib.c:569: warning: incompatible implicit declaration of built-in function ‘memset’
gui_lib.c:626: warning: incompatible implicit declaration of built-in function ‘memcpy’
gui_lib.c:648: warning: incompatible implicit declaration of built-in function ‘memset’
gui_lib.c:662: warning: incompatible implicit declaration of built-in function ‘memcpy’
gui_lib.c:696: warning: incompatible implicit declaration of built-in function ‘memcpy’
gui_lib.c:722: warning: incompatible implicit declaration of built-in function ‘memset’
gui_lib.c: In function ‘old_add_disk_to_raid01’:
gui_lib.c:841: warning: incompatible implicit declaration of built-in function ‘memset’
gui_lib.c:852: warning: incompatible implicit declaration of built-in function ‘memcpy’
gui_lib.c: In function ‘hpt_add_spare_disk’:
gui_lib.c:991: warning: incompatible implicit declaration of built-in function ‘memset’
gui_lib.c: In function ‘hpt_set_array_info’:
gui_lib.c:1023: warning: incompatible implicit declaration of built-in function ‘memset’
gui_lib.c:1024: warning: incompatible implicit declaration of built-in function ‘memcpy’
gui_lib.c:1029: warning: incompatible implicit declaration of built-in function ‘memcpy’
gui_lib.c: In function ‘hpt_default_ioctl’:
gui_lib.c:1232: warning: incompatible implicit declaration of built-in function ‘memset’
In file included from hpt.c:163:
ioctl.c: At top level:
ioctl.c:9: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘DPC_Request_Nums’
ioctl.c:63: error: expected ‘)’ before numeric constant
ioctl.c:67: error: expected ‘)’ before string constant
ioctl.c: In function ‘beeper_timer_fn’:
ioctl.c:87: error: invalid use of undefined type ‘struct timer_list’
ioctl.c:87: error: ‘jiffies’ undeclared (first use in this function)
ioctl.c:88: warning: implicit declaration of function ‘add_timer’
ioctl.c: In function ‘ioctl_ReportEvent’:
ioctl.c:100: warning: incompatible implicit declaration of built-in function ‘memset’
ioctl.c:107: warning: incompatible implicit declaration of built-in function ‘memcpy’
ioctl.c:139: error: invalid use of undefined type ‘struct timer_list’
ioctl.c:140: error: invalid use of undefined type ‘struct timer_list’
ioctl.c:141: error: invalid use of undefined type ‘struct timer_list’
ioctl.c:141: error: ‘jiffies’ undeclared (first use in this function)
ioctl.c: In function ‘verify_vd’:
ioctl.c:164: warning: passing argument 1 of ‘sd_inuse’ from incompatible pointer type
ioctl.c: In function ‘Kernel_DeviceIoControl’:
ioctl.c:215: warning: passing argument 1 of ‘sd_inuse’ from incompatible pointer type
ioctl.c:252: warning: incompatible implicit declaration of built-in function ‘memcpy’
ioctl.c:371: error: ‘driver_lock’ undeclared (first use in this function)
ioctl.c:394: error: ‘jiffies’ undeclared (first use in this function)
ioctl.c:394: error: ‘HZ’ undeclared (first use in this function)
ioctl.c: In function ‘hpt_set_array_state’:
ioctl.c:439: error: ‘jiffies’ undeclared (first use in this function)
ioctl.c:439: error: ‘HZ’ undeclared (first use in this function)
ioctl.c:449: error: ‘driver_lock’ undeclared (first use in this function)
ioctl.c: In function ‘hpt_rescan_all’:
ioctl.c:571: error: ‘driver_lock’ undeclared (first use in this function)
ioctl.c:576: error: ‘jiffies’ undeclared (first use in this function)
ioctl.c:576: error: ‘HZ’ undeclared (first use in this function)
ioctl.c:577: error: dereferencing pointer to incomplete type
ioctl.c:577: error: ‘DPC_Request_Nums’ undeclared (first use in this function)
ioctl.c:583: error: dereferencing pointer to incomplete type
ioctl.c: In function ‘hpt_rebuild_data_block’:
ioctl.c:640: error: storage size of ‘timer’ isn’t known
ioctl.c:641: error: storage size of ‘sem’ isn’t known
ioctl.c:648: error: ‘driver_lock’ undeclared (first use in this function)
ioctl.c:684: warning: implicit declaration of function ‘sema_init’
ioctl.c:690: error: ‘GFP_ATOMIC’ undeclared (first use in this function)
ioctl.c:690: warning: assignment makes pointer from integer without a cast
ioctl.c:740: error: ‘jiffies’ undeclared (first use in this function)
ioctl.c:740: error: ‘HZ’ undeclared (first use in this function)
ioctl.c:827: warning: implicit declaration of function ‘set_current_state’
ioctl.c:827: error: ‘TASK_INTERRUPTIBLE’ undeclared (first use in this function)
ioctl.c:828: warning: implicit declaration of function ‘schedule_timeout’
ioctl.c:883: error: dereferencing pointer to incomplete type
ioctl.c:897: error: ‘DPC_Request_Nums’ undeclared (first use in this function)
ioctl.c:641: warning: unused variable ‘sem’
ioctl.c:640: warning: unused variable ‘timer’
In file included from hpt.c:171:
vdevice.c: In function ‘__fRegisterVDevices’:
vdevice.c:71: warning: incompatible implicit declaration of built-in function ‘memset’
vdevice.c: In function ‘fCheckBootable’:
vdevice.c:188: warning: incompatible implicit declaration of built-in function ‘memset’
vdevice.c: In function ‘AllocateCommand’:
vdevice.c:291: warning: incompatible implicit declaration of built-in function ‘memset’
In file included from hpt.c:172:
init.c: In function ‘InitializeAllChips’:
init.c:18: warning: incompatible implicit declaration of built-in function ‘memset’
init.c: In function ‘fGetChannelTable’:
init.c:129: warning: incompatible implicit declaration of built-in function ‘memset’
init.c: In function ‘fGetDeviceTable’:
init.c:140: warning: incompatible implicit declaration of built-in function ‘memset’

It goes on for some length before returning a: 
make: *** [hpt.o] Error 1

---

