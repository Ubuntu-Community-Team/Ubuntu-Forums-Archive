---
title: "Trouble with Cisco VPN and vpnc"
date: 2005-10-21
forum: Installation &amp; Upgrades
---

### Post by aclonedsheep on 2005-10-21
Hi,

I have essentially exhausted every resource before posting.  I have seen a few other threads on similiar topics; where university students try to get their cisco clinet working and have trouble, but my problems are slightly different.

The installation completes and tells me to run the script to initialize it.

I get this error:
```
Starting /opt/cisco-vpnclient/bin/vpnclient: insmod: error inserting '/lib/modules/2.6.12-9-386/CiscoVPN/cisco_ipsec.ko': -1 Unknown symbol in module
Failed (insmod)

```

When I go back and look at the installation I see the following warnings:

```
make -C /usr/src/linux-headers-2.6.12-9-386/ SUBDIRS=/home/ben/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  Building modules, stage 2.
  MODPOST
Warning: could not find /home/ben/Desktop/vpnclient/.libdriver.so.cmd for /home/ben/Desktop/vpnclient/libdriver.so
*** Warning: "CNI_DNEListBindings" [/home/ben/Desktop/vpnclient/cisco_ipsec.ko] undefined!
*** Warning: "CniGetBindingByIndex" [/home/ben/Desktop/vpnclient/cisco_ipsec.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
Copying module to directory "/lib/modules/2.6.12-9-386/CiscoVPN".
Already have group 'bin'

```

I also installed vpnc hoping the open-source software would work but have not been able to connect...

So I can take either approach...get the cisco client working or properly configure vpnc (I have my pcf file and also data from the network admin)
From his email:
> 1.      Policy: Cisco VPN Concentrator 3000
2.      Gateway Address: [server]
3.      Use Perfect Forward Secrecy: checked
4.      Group Name: [use your imagination]
5.      Group Password: [obviously censored]
6.      Username: zoo account
7.      IKE Crypto Suite:
  a.      Group: GRP2_DH-1024
  b.      Cipher: 3DES_CBC
  c.      Hash: MD5
8.      IPSec Suite: ESPIP_3DES_MD5-96
9.      Query DNS/WINS: checked

pcf file:

```
[main]
Description=Secure connection to internet
Host=[censored]
AuthType=1
GroupName=[censored]
GroupPwd=
enc_GroupPwd=[censored]
EnableISPConnect=0
ISPConnectType=1
ISPConnect=
ISPCommand=
Username=
SaveUserPassword=0
UserPassword=
enc_UserPassword=
NTDomain=
EnableBackup=0
BackupServer=
EnableMSLogon=1
MSLogonType=0
EnableNat=1
TunnelingMode=0
TcpTunnelingPort=10000
CertStore=0
CertName=
CertPath=
CertSubjectName=
CertSerialHash=00000000000000000000000000000000
SendCertChain=0
DHGroup=2
ForceKeepAlives=0
PeerTimeout=90
EnableLocalLAN=0
VerifyCertDN=

```

If anyone could help me with either method so I can get connected to the wireless network...I would greatly appreciate it!  If you want to help me with both, for the sake of learning, that would be cool too ;) 

Ben

---

