---
title: "make: *** [install-generic] Error 1"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by michuroztocz on 2010-05-01
I'm trying to undervolt my CPU (Pentium M 750 in HP Compaq nc4200) in Ubuntu 10.04 with kernel 2.6.32-21. I've made many attempts and solved few problems, but now i'm stuck. I have no idea what to do and what does this error mean. I don't know how to access whole log of operation, so here is everything what I can copy from terminal:
```
                    pcwd / ib700wdt             : char-major-10-130 
                    pcwd / ibmasr               : char-major-10-130 
                    pcwd / wafer5823wdt         : char-major-10-130 
                    pcwd / i6300esb             : char-major-10-130 
                    pcwd / iTCO_wdt             : char-major-10-130 
               intel_rng / iTCO_wdt             : pci:v00008086d000027BDsv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d000027B9sv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d000027B8sv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d0000267Fsv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d0000267Esv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d0000267Dsv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d0000267Csv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d0000267Bsv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d0000267Asv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d00002679sv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d00002678sv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d00002677sv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d00002676sv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d00002675sv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d00002674sv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d00002673sv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d00002672sv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d00002671sv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d00002670sv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d00002641sv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d00002640sv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d000025A1sv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d000024D0sv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d00002450sv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d000024CCsv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d000024C0sv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d0000248Csv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d00002480sv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d0000244Csv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d00002440sv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d00002420sv*sd*bc*sc*i* 
               intel_rng / iTCO_wdt             : pci:v00008086d00002410sv*sd*bc*sc*i* 
                    pcwd / it8712f_wdt          : char-major-10-130 
                    pcwd / it87_wdt             : char-major-10-130 
                    pcwd / sc1200wdt            : char-major-10-130 
                    pcwd / scx200_wdt           : char-major-10-130 
                    pcwd / pc87413_wdt          : char-major-10-130 
                    pcwd / sbc60xxwdt           : char-major-10-130 
                    pcwd / sbc8360              : char-major-10-130 
                    pcwd / sbc7240_wdt          : char-major-10-130 
                    pcwd / cpu5wdt              : char-major-10-130 
                    pcwd / sch311x_wdt          : char-major-10-130 
                    pcwd / smsc37b787_wdt       : char-major-10-130 
                    pcwd / w83627hf_wdt         : char-major-10-130 
                    pcwd / w83697hf_wdt         : char-major-10-130 
                    pcwd / w83697ug_wdt         : char-major-10-130 
                    pcwd / w83877f_wdt          : char-major-10-130 
                    pcwd / w83977f_wdt          : char-major-10-130 
                    pcwd / machzwd              : char-major-10-130 
                    pcwd / sbc_epx_c3           : char-major-10-130 
                    pcwd / softdog              : char-major-10-130 
                  hfcpci / hisax                : pci:v0000114Fd00000073sv*sd*bc*sc*i* 
                  hfcpci / hisax                : pci:v0000114Fd00000072sv*sd*bc*sc*i* 
                  hfcpci / hisax                : pci:v0000114Fd00000071sv*sd*bc*sc*i* 
                  hfcpci / hisax                : pci:v0000114Fd00000070sv*sd*bc*sc*i* 
                  hfcpci / hisax                : pci:v000015B0d00002BD0sv*sd*bc*sc*i* 
                  hfcpci / hisax                : pci:v00001051d00000100sv*sd*bc*sc*i* 
                  hfcpci / hisax                : pci:v00000871d0000FFA1sv*sd*bc*sc*i* 
                  hfcpci / hisax                : pci:v00000871d0000FFA2sv*sd*bc*sc*i* 
                  hfcpci / hisax                : pci:v00001043d00000675sv*sd*bc*sc*i* 
                  hfcpci / hisax                : pci:v000013D1d00002BD1sv*sd*bc*sc*i* 
                  hfcpci / hisax                : pci:v00001397d0000B701sv*sd*bc*sc*i* 
                  hfcpci / hisax                : pci:v00001397d0000B700sv*sd*bc*sc*i* 
                  hfcpci / hisax                : pci:v00001397d0000B100sv*sd*bc*sc*i* 
                  hfcpci / hisax                : pci:v00001397d0000B00Csv*sd*bc*sc*i* 
                  hfcpci / hisax                : pci:v00001397d0000B00Bsv*sd*bc*sc*i* 
                  hfcpci / hisax                : pci:v00001397d0000B00Asv*sd*bc*sc*i* 
                  hfcpci / hisax                : pci:v00001397d0000B009sv*sd*bc*sc*i* 
                  hfcpci / hisax                : pci:v00001397d0000B008sv*sd*bc*sc*i* 
                  hfcpci / hisax                : pci:v00001397d0000B007sv*sd*bc*sc*i* 
                  hfcpci / hisax                : pci:v00001397d0000B006sv*sd*bc*sc*i* 
                  hfcpci / hisax                : pci:v00001397d0000B000sv*sd*bc*sc*i* 
                  hfcpci / hisax                : pci:v00001397d00002BD0sv*sd*bc*sc*i* 
                   w6692 / hisax                : pci:v00001050d00006692sv*sd*bc*sc*i* 
                   w6692 / hisax                : pci:v00000675d00001702sv*sd*bc*sc*i* 
                  netjet / hisax                : pci:v0000E159d00000001sv*sd*bc*sc*i* 
           mISDNinfineon / hisax                : pci:v00001267d00001016sv*sd*bc*sc*i* 
            com20020_pci / hisax                : pci:v000010B5d00009050sv*sd*bc*sc*i* 
           mISDNinfineon / hisax                : pci:v000010B5d00001187sv*sd*bc*sc*i* 
           mISDNinfineon / hisax                : pci:v000010B5d00001151sv*sd*bc*sc*i* 
           mISDNinfineon / hisax                : pci:v000010B5d00001152sv*sd*bc*sc*i* 
           mISDNinfineon / hisax                : pci:v000010B5d00001030sv*sd*bc*sc*i* 
           mISDNinfineon / hisax                : pci:v00001048d00003000sv*sd*bc*sc*i* 
           mISDNinfineon / hisax                : pci:v00001048d00001000sv*sd*bc*sc*i* 
           mISDNinfineon / hisax                : pci:v00001133d0000E00Bsv*sd*bc*sc*i* 
           mISDNinfineon / hisax                : pci:v00001133d0000E005sv*sd*bc*sc*i* 
           mISDNinfineon / hisax                : pci:v00001133d0000E004sv*sd*bc*sc*i* 
           mISDNinfineon / hisax                : pci:v00001133d0000E002sv*sd*bc*sc*i* 
                avmfritz / hisax                : pci:v00001244d00000A00sv*sd*bc*sc*i* 
                 hfcsusb / hfc_usb              : usb:v071Dp1005d*dc*dsc*dp*ic*isc*ip* 
                 hfcsusb / hfc_usb              : usb:v07B0p0006d*dc*dsc*dp*ic*isc*ip* 
                 hfcsusb / hfc_usb              : usb:v07FAp0847d*dc*dsc*dp*ic*isc*ip* 
                 hfcsusb / hfc_usb              : usb:v07FAp0846d*dc*dsc*dp*ic*isc*ip* 
                 hfcsusb / hfc_usb              : usb:v08E3p0301d*dc*dsc*dp*ic*isc*ip* 
                 hfcsusb / hfc_usb              : usb:v0742p200Ad*dc*dsc*dp*ic*isc*ip* 
                 hfcsusb / hfc_usb              : usb:v0742p2009d*dc*dsc*dp*ic*isc*ip* 
                 hfcsusb / hfc_usb              : usb:v0742p2008d*dc*dsc*dp*ic*isc*ip* 
                 hfcsusb / hfc_usb              : usb:v07B0p0007d*dc*dsc*dp*ic*isc*ip* 
                 hfcsusb / hfc_usb              : usb:v0675p1688d*dc*dsc*dp*ic*isc*ip* 
                 hfcsusb / hfc_usb              : usb:v0959p2BD0d*dc*dsc*dp*ic*isc*ip* 
                hfcmulti / hfc4s8s_l1           : pci:v00001397d000016B8sv00001397sd0000B522bc*sc*i* 
                hfcmulti / hfc4s8s_l1           : pci:v00001397d000008B4sv00001397sd0000B520bc*sc*i* 
                hfcmulti / hfc4s8s_l1           : pci:v00001397d000016B8sv00001397sd000016B8bc*sc*i* 
                hfcmulti / hfc4s8s_l1           : pci:v00001397d000008B4sv00001397sd000008B4bc*sc*i* 
                avmfritz / hisax_fcpcipnp       : pci:v00001244d00000E00sv*sd*bc*sc*i* 
                avmfritz / hisax_fcpcipnp       : pci:v00001244d00000A00sv*sd*bc*sc*i* 
                 i5k_amb / i5000_edac           : pci:v00008086d000025F0sv*sd*bc*sc*i* 
                 i5k_amb / i5400_edac           : pci:v00008086d00004030sv*sd*bc*sc*i* 
                aes_i586 / padlock_aes          : aes 
               geode_rng / geode_aes            : pci:v00001022d00002082sv*sd*bc*sc*i* 
INT           prism2_usb / prism2_usb           : usb:v2821p3300d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v1737p0077d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v7392p7717d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v0789p0164d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v0789p0163d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v0789p0162d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v7392p7711d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v1740p9703d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v1740p9702d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v1740p9701d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v0586p3416d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v083ApA618d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v083ApB522d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v050Dp825Ad*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v2019pED06d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v1737p0070d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v1737p0071d*dc*dsc*dp*ic*isc*ip* 
               rt2800usb / rt2870sta            : usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip* 
              serqt_usb2 / quatech_usb2         : usb:v061DpC180d*dc*dsc*dp*ic*isc*ip* 
              serqt_usb2 / quatech_usb2         : usb:v061DpC1A0d*dc*dsc*dp*ic*isc*ip* 
              serqt_usb2 / quatech_usb2         : usb:v061DpC170d*dc*dsc*dp*ic*isc*ip* 
              serqt_usb2 / quatech_usb2         : usb:v061DpC160d*dc*dsc*dp*ic*isc*ip* 
              serqt_usb2 / quatech_usb2         : usb:v061DpC150d*dc*dsc*dp*ic*isc*ip* 
              serqt_usb2 / quatech_usb2         : usb:v061DpC140d*dc*dsc*dp*ic*isc*ip* 
              serqt_usb2 / quatech_usb2         : usb:v061DpC120d*dc*dsc*dp*ic*isc*ip* 
           Bell*:pnDOA*: / Bell*:pnAOA*:        : dmi:*:*Packard 
                via_ircc / parport_pc           : pci:v00001106d00008231sv*sd*bc*sc*i* 
               i2c_piix4 / scb2_flash           : pci:v00001166d00000201sv*sd*bc*sc*i* 
INT              mtdchar / mtdchar              : char-major-90-* 
                ohci1394 / firewire_ohci        : pci:v*d*sv*sd*bc0Csc00i10* 
                    sbp2 / firewire_sbp2        : ieee1394:ven*mo*sp0000609Ever00010483* 
                 eth1394 / firewire_net         : ieee1394:ven*mo*sp0000005Ever00000001* 
                whci_hcd / whci                 : pci:v*d*sv*sd*bc0Dsc10i10* 
                whci_hcd / whc_rc               : pci:v*d*sv*sd*bc0Dsc10i10* 
           matroxfb_base / matrox_w1            : pci:v0000102Bd00000525sv*sd*bc*sc*i* 
                  pcspkr / snd_pcsp             : platform:pcspkr 
                      sb / snd_als100           : acpi*:@@@0020:* 
                      sb / snd_als100           : pnp:d@@@0020* 
                      sb / snd_als100           : acpi*:@X@2001:* 
                      sb / snd_als100           : pnp:d@X@2001* 
                      sb / snd_als100           : acpi*:@@@2001:* 
                      sb / snd_als100           : pnp:d@@@2001* 
                      sb / snd_als100           : acpi*:@X@1001:* 
                      sb / snd_als100           : pnp:d@X@1001* 
                      sb / snd_als100           : acpi*:@@@1001:* 
                      sb / snd_als100           : pnp:d@@@1001* 
                      sb / snd_als100           : acpi*:@H@0001:* 
                      sb / snd_als100           : pnp:d@H@0001* 
                      sb / snd_als100           : acpi*:@X@0001:* 
                      sb / snd_als100           : pnp:d@X@0001* 
                      sb / snd_als100           : acpi*:@@@0001:* 
                      sb / snd_als100           : pnp:d@@@0001* 
                      sb / snd_cmi8330          : acpi*:@H@0001:* 
                      sb / snd_cmi8330          : pnp:d@H@0001* 
                      sb / snd_cmi8330          : acpi*:@@@0001:* 
                      sb / snd_cmi8330          : pnp:d@@@0001* 
                      sb / snd_cmi8330          : acpi*:@X@0001:* 
                      sb / snd_cmi8330          : pnp:d@X@0001* 
                      sb / snd_dt019x           : acpi*:@H@0001:* 
                      sb / snd_dt019x           : pnp:d@H@0001* 
                      sb / snd_dt019x           : acpi*:@X@0001:* 
                      sb / snd_dt019x           : pnp:d@X@0001* 
                      sb / snd_dt019x           : acpi*:@@@0001:* 
                      sb / snd_dt019x           : pnp:d@@@0001* 
                      sb / snd_es18xx           : acpi*:ESS1879:* 
                      sb / snd_es18xx           : pnp:dESS1879* 
                      sb / snd_es18xx           : acpi*:ESS1878:* 
                      sb / snd_es18xx           : pnp:dESS1878* 
                      sb / snd_es18xx           : acpi*:ESS1869:* 
                      sb / snd_es18xx           : pnp:dESS1869* 
                      sb / snd_es18xx           : acpi*:ESS8611:* 
                      sb / snd_es18xx           : pnp:dESS8611* 
                      sb / snd_es18xx           : acpi*:ESS1868:* 
                      sb / snd_es18xx           : pnp:dESS1868* 
                      sb / snd_es18xx           : acpi*:ESS1879:* 
                      sb / snd_es18xx           : pnp:dESS1879* 
                      sb / snd_es18xx           : acpi*:ESS1869:* 
                      sb / snd_es18xx           : pnp:dESS1869* 
INT          snd_opl3sa2 / snd_opl3sa2          : acpi*:NMX2210:* 
INT          snd_opl3sa2 / snd_opl3sa2          : pnp:dNMX2210* 
INT          snd_opl3sa2 / snd_opl3sa2          : acpi*:YMH0021:* 
INT          snd_opl3sa2 / snd_opl3sa2          : pnp:dYMH0021* 
              snd_mpu401 / snd_cs4236           : acpi*:PNPB006:* 
              snd_mpu401 / snd_cs4236           : pnp:dPNPb006* 
INT           snd_cs4236 / snd_cs4236           : acpi*:CSC0000:* 
INT           snd_cs4236 / snd_cs4236           : pnp:dCSC0000* 
INT           snd_cs4236 / snd_cs4236           : acpi*:CSC0100:* 
INT           snd_cs4236 / snd_cs4236           : pnp:dCSC0100* 
           snd_interwave / snd_interwave_stb    : acpi*:ADV0010:* 
           snd_interwave / snd_interwave_stb    : pnp:dADV0010* 
       snd_msnd_pinnacle / snd_msnd_classic     : acpi*:TBS0001:* 
       snd_msnd_pinnacle / snd_msnd_classic     : pnp:dTBS0001* 
       snd_msnd_pinnacle / snd_msnd_classic     : acpi*:TBS0000:* 
       snd_msnd_pinnacle / snd_msnd_classic     : pnp:dTBS0000* 
      snd_opti92x_ad1848 / snd_opti92x_cs4231   : acpi*:OPT9250:* 
      snd_opti92x_ad1848 / snd_opti92x_cs4231   : pnp:dOPT9250* 
      snd_opti92x_ad1848 / snd_opti92x_cs4231   : acpi*:OPT0002:* 
      snd_opti92x_ad1848 / snd_opti92x_cs4231   : pnp:dOPT0002* 
      snd_opti92x_ad1848 / snd_opti92x_cs4231   : acpi*:OPT0000:* 
      snd_opti92x_ad1848 / snd_opti92x_cs4231   : pnp:dOPT0000* 
      snd_opti92x_ad1848 / snd_opti93x          : acpi*:OPT0002:* 
      snd_opti92x_ad1848 / snd_opti93x          : pnp:dOPT0002* 
                      sb / snd_sb16             : acpi*:PNPB003:* 
                      sb / snd_sb16             : pnp:dPNPb003* 
                      sb / snd_sb16             : acpi*:CTL0043:* 
                      sb / snd_sb16             : pnp:dCTL0043* 
                      sb / snd_sb16             : acpi*:CTL0041:* 
                      sb / snd_sb16             : pnp:dCTL0041* 
                      sb / snd_sb16             : acpi*:CTL0001:* 
                      sb / snd_sb16             : pnp:dCTL0001* 
                      sb / snd_sb16             : acpi*:CTL0031:* 
                      sb / snd_sb16             : pnp:dCTL0031* 
                      sb / snd_sbawe            : acpi*:CTL0045:* 
                      sb / snd_sbawe            : pnp:dCTL0045* 
                      sb / snd_sbawe            : acpi*:CTL0044:* 
                      sb / snd_sbawe            : pnp:dCTL0044* 
                      sb / snd_sbawe            : acpi*:CTL0042:* 
                      sb / snd_sbawe            : pnp:dCTL0042* 
                      sb / snd_sbawe            : acpi*:CTL0041:* 
                      sb / snd_sbawe            : pnp:dCTL0041* 
                      sb / snd_sbawe            : acpi*:CTL0031:* 
                      sb / snd_sbawe            : pnp:dCTL0031* 
              snd_mpu401 / snd_wavefront        : acpi*:PNPB006:* 
              snd_cs4236 / snd_wavefront        : acpi*:CSC0010:* 
              snd_cs4236 / snd_wavefront        : pnp:dCSC0010* 
              snd_cs4236 / snd_wavefront        : acpi*:CSC0000:* 
              snd_cs4236 / snd_wavefront        : pnp:dCSC0000* 
                  kahlua / snd_cs5530           : pci:v00001078d00000103sv*sd*bc*sc*i* 
           radio_maestro / snd_es1968           : pci:v0000125Dd00001978sv*sd*bc04sc01i* 
           radio_maestro / snd_es1968           : pci:v0000125Dd00001968sv*sd*bc04sc01i* 
                     mxb / snd_aw2              : pci:v00001131d00007146sv00000000sd00000000bc*sc*i* 
              snd_hifier / snd_oxygen           : pci:v000013F6d00008788sv000013F6sd00008788bc*sc*i* 
              snd_hifier / snd_virtuoso         : pci:v000013F6d00008788sv000013F6sd00008788bc*sc*i* 
             ati_remote2 / lirc_atiusb          : usb:v0471p0602d*dc*dsc*dp*ic*isc*ip* 
              ati_remote / lirc_atiusb          : usb:v0BC7p0006d*dc*dsc*dp*ic*isc*ip* 
              ati_remote / lirc_atiusb          : usb:v0BC7p0004d*dc*dsc*dp*ic*isc*ip* 
              ati_remote / lirc_atiusb          : usb:v0BC7p0002d*dc*dsc*dp*ic*isc*ip* 
make: *** [install-generic] Error 1
forteller@forteller-laptop:/media/sda3/uvolt/linux-2.6.32$ ls
arch     debian         fs       kernel       net             security  virt
block    debian.master  include  lib          README          sound
COPYING  Documentation  init     MAINTAINERS  REPORTING-BUGS  tools
CREDITS  drivers        ipc      Makefile     samples         ubuntu
crypto   firmware       Kbuild   mm           scripts         usr
forteller@forteller-laptop:/media/sda3/uvolt/linux-2.6.32$ 
```

I'm following these tutorials: [https://wiki.ubuntu.com/UndervoltingHowto](https://wiki.ubuntu.com/UndervoltingHowto) [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile), and patch from [this](http://www.linux-phc.org/forum/viewtopic.php?f=13&t=38) topic (post #2).

I will provide additional info if needed. Thanks in advance!

PS. I'm newbie :)

---

