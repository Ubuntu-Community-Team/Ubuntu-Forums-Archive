---
title: "Wondering About My Services"
date: 2010-03-02
forum: Installation &amp; Upgrades
---

### Post by Laysan_A on 2010-03-02
Hi, I just upgraded to karmic. I was playing with reconfiguring my lm_sensors config and the system didn't recognize it. I did a "sudo services --status-all" in terminal and this was the output. There are a lot of question marks, aren't there? Does this look okay?

```
[ - ]  NetworkManager.dpkg-backup                                     
 [ ? ]  acpi-support                                                   
 [ ? ]  acpid                                                          
 [ ? ]  alsa-utils                                                     
 [ ? ]  anacron                                                        
 [ + ]  apparmor                                                       
 [ ? ]  apport                                                         
 [ ? ]  atd                                                            
 [ ? ]  atieventsd                                                     
 [ ? ]  avahi-daemon                                                   
 [ ? ]  binfmt-support                                                 
 [ + ]  blockcontrol                                                   
 [ - ]  bluetooth                                                      
 [ - ]  bootlogd                                                       
 [ - ]  brltty                                                         
 [ + ]  clamav-daemon                                                  
 [ + ]  clamav-freshclam                                               
 [ ? ]  clamsmtp                                                       
 [ ? ]  console-setup                                                  
 [ ? ]  cron                                                           
 [ ? ]  cryptdisks                                                     
 [ ? ]  cryptdisks-early                                               
 [ ? ]  cryptdisks-enable                                              
 [ ? ]  cryptdisks-udev                                                
 [ + ]  cups                                                           
 [ ? ]  dbus                                                           
 [ - ]  dkms_autoinstaller                                             
 [ ? ]  dmesg                                                          
 [ ? ]  dns-clean                                                      
 [ + ]  exim4                                                          
 [ ? ]  failsafe-x                                                     
 [ ? ]  fancontrol                                                     
 [ ? ]  fwlogwatch                                                     
 [ ? ]  gdm                                                            
 [ - ]  grub-common                                                    
 [ ? ]  guarddog                                                       
 [ ? ]  hal                                                            
 [ ? ]  hddtemp                                                        
 [ ? ]  hotkey-setup                                                   
 [ ? ]  hwclock                                                        
 [ ? ]  hwclock-save                                                   
 [ ? ]  hwclock.sh.dpkg-obsolete                                       
 [ ? ]  jackd                                                          
 [ ? ]  kdm                                                            
 [ - ]  kerneloops                                                     
 [ ? ]  keyboard-setup                                                 
 [ ? ]  killprocs                                                      
 [ - ]  klogd                                                          
 [ - ]  laptop-mode                                                    
 [ ? ]  linux-restricted-modules-common                                
 [ ? ]  lm-sensors                                                     
 [ ? ]  module-init-tools                                              
 [ ? ]  mysql                                                          
 [ ? ]  mysql-ndb                                                      
 [ ? ]  mysql-ndb-mgm                                                  
 [ ? ]  network-interface                                              
 [ ? ]  network-manager                                                
 [ ? ]  networking                                                     
 [ ? ]  ondemand                                                       
 [ ? ]  open-vm-tools                                                  
 [ ? ]  pcmciautils                                                    
 [ ? ]  policykit                                                      
 [ ? ]  powernowd                                                      
 [ ? ]  powernowd.early                                                
 [ ? ]  pppd-dns                                                       
 [ ? ]  procps                                                         
 [ + ]  pulseaudio                                                     
 [ ? ]  rc.local                                                       
 [ ? ]  readahead                                                      
 [ ? ]  readahead-desktop                                              
 [ - ]  rsync                                                          
 [ ? ]  rsyslog                                                        
 [ ? ]  rsyslog-kmsg                                                   
 [ + ]  rtirq                                                          
 [ + ]  samba
 [ - ]  saned
 [ ? ]  screen-cleanup
 [ ? ]  sendsigs
 [ ? ]  speech-dispatcher
 [ ? ]  stop-bootlogd
 [ ? ]  stop-bootlogd-single
 [ ? ]  stop-readahead
 [ - ]  sysklogd
 [ + ]  timidity
 [ ? ]  udev
 [ ? ]  udev-finish
 [ ? ]  udevmonitor
 [ ? ]  udevtrigger
 [ ? ]  ufw
 [ ? ]  umountfs
 [ ? ]  umountnfs.sh
 [ ? ]  umountroot
 [ ? ]  unattended-upgrades
 [ - ]  urandom
 [ ? ]  usplash
 [ + ]  vmware
 [ + ]  winbind
 [ ? ]  wpa-ifupdown
 [ - ]  x11-common
```

Thanks!

---

