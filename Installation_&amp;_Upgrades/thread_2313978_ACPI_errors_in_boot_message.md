---
title: "ACPI errors in boot message"
date: 2016-02-17
forum: Installation &amp; Upgrades
---

### Post by lesliek2 on 2016-02-17
I upgraded from 12.04 to 14.04 on an HP Pavilion dv7 laptop. Now I get the following messages on booting up:

[   29.129082] ACPI Warning: 0x0000000000000b00-0x0000000000000b07 SystemIO conflicts with Region \_SB_.PCI0.SMBS.SMBI 1 (20131115/utaddress-251)
[   29.129091] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
...
[   29.373313] ACPI Error: Field [D128] at 1040 exceeds Buffer [NULL] size 160 (bits) (20131115/dsopcode-236)
[   29.373321] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWMC] (Node ffff880119da4320), AE_AML_BUFFER_LIMIT (20131115/psparse-536)
[   29.373330] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node ffff880119da4500), AE_AML_BUFFER_LIMIT (20131115/psparse-536)
[   29.373362] ACPI Error: Field [D128] at 1040 exceeds Buffer [NULL] size 160 (bits) (20131115/dsopcode-236)
[   29.373366] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWMC] (Node ffff880119da4320), AE_AML_BUFFER_LIMIT (20131115/psparse-536)
[   29.373371] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node ffff880119da4500), AE_AML_BUFFER_LIMIT (20131115/psparse-536)
[   29.373437] input: HP WMI hotkeys as /devices/virtual/input/input14
[   29.373691] ACPI Error: Field [D128] at 1040 exceeds Buffer [NULL] size 160 (bits) (20131115/dsopcode-236)
[   29.373699] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWMC] (Node ffff880119da4320), AE_AML_BUFFER_LIMIT (20131115/psparse-536)
[   29.373708] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node ffff880119da4500), AE_AML_BUFFER_LIMIT (20131115/psparse-536)
[   29.373738] ACPI Error: Field [D128] at 1040 exceeds Buffer [NULL] size 160 (bits) (20131115/dsopcode-236)
[   29.373741] ACPI Error: Method parse/execution failed [\_SB_.WMID.HWMC] (Node ffff880119da4320), AE_AML_BUFFER_LIMIT (20131115/psparse-536)
[   29.373747] ACPI Error: Method parse/execution failed [\_SB_.WMID.WMAD] (Node ffff880119da4500), AE_AML_BUFFER_LIMIT (20131115/psparse-536)

Can anyone explain to me in simple language what this set of three error messages repeated four times means?

Is there a way I can fix the errors short of turning off ACPI? (Upgrading the BIOS isn't even a possible option, so far as I can tell.)

If the only way to get rid of the messages is to turn off ACPI at boot up, what are the pros and cons of doing that?

Thank you,

Leslie

---

