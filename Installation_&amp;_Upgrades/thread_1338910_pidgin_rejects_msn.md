---
title: "pidgin rejects msn"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by mv540compaq on 2009-11-26
I am using Pidgin on Gutsy gibbin for my msn account and my gtalk account. for a while now (several months) msn doesn't work.

I checked the debug window:
(17:36:23) jabber: jabber_actions: have pep: NO
(17:36:23) account: Connecting to account [email]ddr_ram2@hotmail.com[/email]
(17:36:23) connection: Connecting. gc = 0x8754300
(17:36:23) msn: new httpconn (0x87a39c8)
(17:36:23) dns: DNS query for 'messenger.hotmail.com' queued
(17:36:23) dns: Created new DNS child 7253, there are now 1 children.
(17:36:23) dns: Successfully sent DNS request to child 7253
(17:36:24) dns: Got response for 'messenger.hotmail.com'
(17:36:24) dnsquery: IP resolved for messenger.hotmail.com
(17:36:24) proxy: Attempting connection to 64.4.50.62
(17:36:24) proxy: Connecting to messenger.hotmail.com:1863 with no proxy
(17:36:24) proxy: Connection in progress
(17:36:24) proxy: Connected to messenger.hotmail.com:1863.
(17:36:24) msn: C: NS 000: VER 1 MSNP9 MSNP8 CVR0
(17:36:24) msn: S: NS 000: VER 1 MSNP9
(17:36:24) msn: C: NS 000: CVR 2 0x0409 winnt 5.1 i386 MSNMSGR 6.0.0602 MSMSGS [email]ddr_ram2@hotmail.com[/email]
(17:36:24) msn: S: NS 000: CVR 2 14.0.8089 14.0.8089 14.0.8089 [http://msgruser.dlservice.microsoft.com/download/7/5/8/758BFCC9-1744-48F7-8162-E0AC1E7BF5C8/en/wlsetup-cvr.exe](http://msgruser.dlservice.microsoft.com/download/7/5/8/758BFCC9-1744-48F7-8162-E0AC1E7BF5C8/en/wlsetup-cvr.exe) [http://download.live.com/?sku=messenger](http://download.live.com/?sku=messenger)
(17:36:24) msn: C: NS 000: USR 3 TWN I [email]ddr_ram2@hotmail.com[/email]
(17:36:25) msn: S: NS 000: XFR 3 NS 207.46.124.62:1863 0 64.4.9.254:1863
(17:36:25) dns: DNS query for '207.46.124.62' queued
(17:36:25) dns: Created new DNS child 7255, there are now 1 children.
(17:36:25) dns: Successfully sent DNS request to child 7255
(17:36:25) dns: Got response for '207.46.124.62'
(17:36:25) dnsquery: IP resolved for 207.46.124.62
(17:36:25) proxy: Attempting connection to 207.46.124.62
(17:36:25) proxy: Connecting to 207.46.124.62:1863 with no proxy
(17:36:25) proxy: Connection in progress
(17:36:25) proxy: Connected to 207.46.124.62:1863.
(17:36:25) msn: C: NS 000: VER 4 MSNP9 MSNP8 CVR0
(17:36:25) dbus: Need to register an object with the dbus subsystem. (If you are not a developer, please ignore this message.)
(17:36:25) dbus: The signal "drawing-tooltip" caused some dbus error. (If you are not a developer, please ignore this message.)
(17:36:25) msn: S: NS 000: VER 4 MSNP9
(17:36:25) msn: C: NS 000: CVR 5 0x0409 winnt 5.1 i386 MSNMSGR 6.0.0602 MSMSGS [email]ddr_ram2@hotmail.com[/email]
(17:36:25) msn: S: NS 000: CVR 5 14.0.8089 14.0.8089 14.0.8089 [http://msgruser.dlservice.microsoft.com/download/7/5/8/758BFCC9-1744-48F7-8162-E0AC1E7BF5C8/en/wlsetup-cvr.exe](http://msgruser.dlservice.microsoft.com/download/7/5/8/758BFCC9-1744-48F7-8162-E0AC1E7BF5C8/en/wlsetup-cvr.exe) [http://download.live.com/?sku=messenger](http://download.live.com/?sku=messenger)
(17:36:25) msn: C: NS 000: USR 6 TWN I [email]ddr_ram2@hotmail.com[/email]
(17:36:25) msn: S: NS 000: USR 6 TWN S ct=1259296584,rver=5.5.4182.0,wp=FS_40SEC_0_COMPACT,lc=1033,id=507,ru=http:%2F%2Fmessenger.msn.com,tw=0,kpp=1,kv=4,ver=2.1.6000.1,rn=1lgjBfIL,tpf=b0735e3a873dfb5e75054465196398e0
(17:36:25) dns: DNS query for 'nexus.passport.com' queued
(17:36:25) dns: Created new DNS child 7257, there are now 1 children.
(17:36:25) dns: Successfully sent DNS request to child 7257
(17:36:26) dns: Got response for 'nexus.passport.com'
(17:36:26) dnsquery: IP resolved for nexus.passport.com
(17:36:26) proxy: Attempting connection to 65.54.254.139
(17:36:26) proxy: Connecting to nexus.passport.com:443 with no proxy
(17:36:26) proxy: Connection in progress
(17:36:26) proxy: Connected to nexus.passport.com:443.
(17:36:26) nss: subject=CN=nexus.passport.com,OU=MSN Passport,O=Microsoft,L=Redmond,ST=Washington,C=US issuer=CN=VeriSign Class 3 Secure Server CA,OU=Terms of use at [https://www.verisign.com/rpa](https://www.verisign.com/rpa) (c)05,OU=VeriSign Trust Network,O="VeriSign, Inc.",C=US
(17:36:26) nss: partial certificate chain
(17:36:26) certificate/x509/tls_cached: Starting verify for nexus.passport.com
(17:36:26) certificate/x509/tls_cached: Checking for cached cert...
(17:36:26) certificate/x509/tls_cached: ...Found cached cert
(17:36:26) nss/x509: Loading certificate from /home/martin/.purple/certificates/x509/tls_peers/nexus.passport.com
(17:36:26) certificate/x509/tls_cached: Peer cert did NOT match cached
(17:36:26) certificate/x509/tls_cached: Certificate for nexus.passport.com does not match cached. Auto-rejecting!
(17:36:26) msn: C: NS 000: OUT
(17:36:26) jabber: jabber_actions: have pep: NO
(17:36:26) account: Disconnecting account 0x81a8ee0
(17:36:26) connection: Disconnecting connection 0x8754300
(17:36:26) msn: destroy httpconn (0x87a39c8)
(17:36:26) jabber: jabber_actions: have pep: NO
(17:36:26) connection: Destroying connection 0x8754300
(17:36:28) util: Writing file accounts.xml to directory /home/martin/.purple
(17:36:28) util: Writing file /home/martin/.purple/accounts.xml

Any and all help much apreciated

---

### Post by gnssw on 2010-02-05
Hi!

Could you solve this? I'm having the same problem...

---

