---
title: "Could someone be so kind to post whats in your /etc/rc2.d?"
date: 2010-02-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Vanishing on 2010-02-07
Mine got cleared somehow by ntp...
just wanna see what is enabled there for default.
thanks

---

### Post by MacUntu on 2010-02-07
Pretty fresh vbox installation:

S20fancontrol
S20kerneloops
S20speech-dispatcher
S25bluetooth
S50cups
S50pulseaudio
S50rsync
S50saned
S70dns-clean
S70pppd-dns
S90binfmt-support
S99acpi-support
S99grub-common
S99ondemand
S99rc.local

---

### Post by ranch hand on 2010-02-07
Badly hacked OS with 2.6.33-999 kernel;

K01gdm               K20xinetd                           S15wpa-ifupdown
K01timidity          K25hwclock.sh                       S20sendsigs
K02usplash           K31atieventsd                       S30urandom
K20apport            K50alsa-utils                       S31umountnfs.sh
K20boinc-client      K63mountoverflowtmp                 S35networking
K20clamav-freshclam  K74bluetooth                        S40umountfs
K20exim4             K99laptop-mode                      S60umountroot
K20wifi-radar        README                              S89casper
K20winbind           S01linux-restricted-modules-common  S90halt

EDIT

Ignore that it is mixed with the one from this OS (9.04).  I checked and mine matchs the one posted by MacUntu.

Sorry if that gave you a heart attach.  It about did me in.

---

### Post by VMC on 2010-02-07
> **MacUntu said:**
> Pretty fresh vbox installation:

S20fancontrol
S20kerneloops
S20speech-dispatcher
S25bluetooth
S50cups
S50pulseaudio
S50rsync
S50saned
S70dns-clean
S70pppd-dns
S90binfmt-support
S99acpi-support
S99grub-common
S99ondemand
S99rc.local

I have the same as yours, and mine is from current Feb5.

---

### Post by Reiger on 2010-02-08
```

README         
S20kerneloops  
S20winbind   
S25bluetooth  
S50rsync  
S70dns-clean  
S90binfmt-support  
S99acpi-support  
S99ondemand
S20fancontrol  
S20wicd        
S21sendmail  
S50cups       
S50saned  
S70pppd-dns   
S91apache2         
S99grub-common   
S99rc.local

```

Although apache2, and sendmail and wicd are not part of a default installation.

---

### Post by pastalavista on 2010-02-08
> README                 S20postfix            S50pulseaudio      S99acpi-support
S20atop                S20speech-dispatcher  S50rsync           S99grub-common
S20dkms_autoinstaller  S20winbind            S50saned           S99laptop-mode
S20fancontrol          S25bluetooth          S70dns-clean       S99ondemand
S20hostapd             S31atieventsd         S70pppd-dns        S99rc.local
S20kerneloops          S50cups               S90binfmt-support

only thing not default, as far as I know, is 'atop'

---

