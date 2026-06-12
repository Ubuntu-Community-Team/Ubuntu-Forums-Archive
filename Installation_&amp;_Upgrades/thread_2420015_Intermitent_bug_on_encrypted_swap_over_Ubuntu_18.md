---
title: "Intermitent bug on encrypted swap over Ubuntu 18"
date: 2019-05-28
forum: Installation &amp; Upgrades
---

### Post by paul942 on 2019-05-28
I need encrypt swap with a fixed key as following but each time I boot it behave differently one itmes it works one times it crash.  
With SSD is easier clean a key if necessary than clean the device itself.  

```
   sudo -i
    cd /root 
    mkdir -p ./.myfolder 
    cd ./.myfolder 
    swapsize='4G' 
    curdir=$(pwd) 
    flNmDev="myfile"
    flPtDev="$curdir/$flNmDev" 
    flNmKey="mykeyfile" 
    flPtKey="$curdir/$flNmKey" 
    flNmMnt="mydevname" 
    flPtMnt="$curdir/$flNmMnt" 
    fallocate -l $swapsize $flPtDev &> /dev/null
    chmod 0600 $flPtDev
    chown root $flPtDev 
    dd if=/dev/urandom of=$flPtKey bs=4096 count=1 conv=notrunc,noerror &> /dev/null 
    sudo chmod 0600 $flPtKey
    chown root $flPtKey
cat << EOF > /etc/crypttab
# <target name> <source device>         <key file>      <options>
$flNmMnt $flPtDev $flPtKey swap,offset=1024,cipher=aes-xts-plain64
EOF
    cryptdisks_start $flNmMnt &> /dev/null
    mappedCryptPath="/dev/mapper/$flNmMnt"
    mkswap -L swapone $mappedCryptPath -f &> /dev/null
    rpl "/swap.img" "#/swap.img" /etc/fstab &> /dev/null
    echo "$mappedCryptPath none swap sw 0 0" >> /etc/fstab
    swapon -a 
```

On the same machine and same Version of Ubuntu it sometimes works **but** sometimes crash on boot.
Following some output on each boot it did:

```

uname -v

#54-Ubuntu SMP Mon May 6 18:46:08 UTC 2019
```

```

journalctl -b

 systemd[1]: Mounting /boot...
swapon[995]: swapon: /dev/mapper/mydevname: swapon failed: Device or resource busy
mkswap[991]: mkswap: unable to erase bootbits sectors
 systemd[1]: systemd-cryptsetup@mydevname.service: Control process exited, code=exited status=1
 systemd[1]: systemd-cryptsetup@mydevname.service: Failed with result 'exit-code'.
 systemd[1]: Failed to start Cryptography Setup for mydevname.
 systemd[1]: Dependency failed for Local Encrypted Volumes.
 systemd[1]: cryptsetup.target: Job cryptsetup.target/start failed with result 'dependency'.
 systemd[1]: dev-mapper-mydevname.swap: Swap process exited, code=exited status=255
 systemd[1]: dev-mapper-mydevname.swap: Failed with result 'exit-code'.
 systemd[1]: Failed to activate swap /dev/mapper/mydevname.
 systemd[1]: Dependency failed for Swap.
 systemd[1]: swap.target: Job swap.target/start failed with result 'dependency'.
```


[/CODE]```


cat /proc/meminfo | grep Sw

SwapCached:            0 kB
SwapTotal:             0 kB
SwapFree:              0 kB
  
``````


  cat /proc/swaps 

Filename                Type        Size    Used    Priority
  
``````


  cat /proc/swaps 

Filename                Type        Size    Used    Priority
/dev/dm-1                               partition   4193788 72704   -2
  
``````


  cat /proc/meminfo | grep Sw

SwapCached:        10644 kB
SwapTotal:       4193788 kB
SwapFree:        4102396 kB
  
``````


  journalctl -b

mkswap[868]: mkswap: /dev/mapper/mydevname: warning: wiping old swap signature.
systemd[1]: Found device /dev/mapper/mydevname.
systemd[1]: Activating swap /dev/mapper/mydevname...
mkswap[868]: Setting up swapspace version 1, size = 4 GiB (4294438912 bytes)
mkswap[868]: no label, UUID=348deb8f-7457-4829-a1a2-0ebd1b61f6d6
systemd[1]: Started Cryptography Setup for mydevname.
systemd[1]: Reached target Local Encrypted Volumes.
kernel: Adding 4193788k swap on /dev/mapper/mydevname.  Priority:-2 extents:1 across:4193788k FS
systemd[1]: Activated swap /dev/mapper/mydevname.
systemd[1]: Reached target Swap.
  
``````


  cat /proc/swaps 

Filename                Type        Size    Used    Priority
/dev/dm-1                               partition   4193788 0   -2
  
``````


  journalctl -b

mkswap[683]: mkswap: unable to erase bootbits sectors
systemd[1]: systemd-cryptsetup@mydevname.service: Control process exited, code=exited status=1
systemd[1]: systemd-cryptsetup@mydevname.service: Failed with result 'exit-code'.
systemd[1]: Failed to start Cryptography Setup for mydevname.
systemd[1]: Dependency failed for Local Encrypted Volumes.
systemd[1]: cryptsetup.target: Job cryptsetup.target/start failed with result 'dependency'.
systemd[1]: Dependency failed for dev-mapper-mydevname.device.
systemd[1]: Dependency failed for /dev/mapper/mydevname.
systemd[1]: Dependency failed for Swap.
systemd[1]: swap.target: Job swap.target/start failed with result 'dependency'.
systemd[1]: dev-mapper-mydevname.swap: Job dev-mapper-mydevname.swap/start failed with result 'dependency'.
systemd[1]: dev-mapper-mydevname.device: Job dev-mapper-mydevname.device/start failed with result 'dependency'.
systemd[1]: Activating swap /dev/mapper/mydevname...
systemd[1]: Starting Cryptography Setup for mydevname...
systemd-cryptsetup[688]: Volume mydevname already active.
kernel: Adding 4193788k swap on /dev/mapper/mydevname.  Priority:-2 extents:1 across:4193788k FS
systemd[1]: Activated swap /dev/mapper/mydevname.
mkswap[690]: mkswap: error: /dev/mapper/mydevname is mounted; will not make swapspace
systemd[1]: systemd-cryptsetup@mydevname.service: Control process exited, code=exited status=1
systemd[1]: systemd-cryptsetup@mydevname.service: Failed with result 'exit-code'.
systemd[1]: Failed to start Cryptography Setup for mydevname.
  
``````


  cat /proc/meminfo | grep Sw

SwapCached:            0 kB
SwapTotal:       4193788 kB
SwapFree:        4193788 kB



```

---

