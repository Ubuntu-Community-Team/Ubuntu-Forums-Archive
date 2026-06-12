---
title: "Ubuntu server 22.04.2 LTS (Gluster 11 + nfs-ganesha)"
date: 2023-04-09
forum: Installation &amp; Upgrades
---

### Post by mirino on 2023-04-09
[COLOR=#000000]Hello ,[/COLOR]

[COLOR=#000000]I am trying to start a nfs-ganesha server with a Gluster folder on [/COLOR][COLOR=#000000]Ubuntu server 22.04.2 LTS arm64 Raspberry PI 4[/COLOR]
[COLOR=#000000]I keep getting the following error but I have installed required packages...[/COLOR]

***_Error:_***
[COLOR=#000000]/lib/aarch64-linux-gnu/libtcmalloc_minimal.so.4: cannot allocate memory in static TLS block. You might want to install the nfs-ganesha-GLUSTER package[/COLOR]


***[COLOR=#000000]grep " install " /var/log/dpkg.log[/COLOR]***

[COLOR=#000000]2023-04-05 20:25:19 install nfs-ganesha:arm64 <none> 3.5-1ubuntu1[/COLOR]
[COLOR=#000000]2023-04-05 20:25:20 install nfs-ganesha-gluster:arm64 <none> 3.5-1ubuntu1
[/COLOR][B]
*gluster --version*[/B]
glusterfs 11.0

***[COLOR=#000000]/var/log/ganesha/ganesha.log[/COLOR]***
```
09/04/2023 19:48:06 : epoch 6432fa56 : raspberry2 : ganesha.nfsd-3528203[main] main :MAIN :EVENT :ganesha.nfsd Starting: Ganesha Version 3.5
09/04/2023 19:48:06 : epoch 6432fa56 : raspberry2 : ganesha.nfsd-3528204[main] nfs_set_param_from_conf :NFS STARTUP :EVENT :Configuration file successfully parsed
09/04/2023 19:48:06 : epoch 6432fa56 : raspberry2 : ganesha.nfsd-3528204[main] init_server_pkgs :NFS STARTUP :EVENT :Initializing ID Mapper.
09/04/2023 19:48:06 : epoch 6432fa56 : raspberry2 : ganesha.nfsd-3528204[main] init_server_pkgs :NFS STARTUP :EVENT :ID Mapper successfully initialized.
09/04/2023 19:48:07 : epoch 6432fa56 : raspberry2 : ganesha.nfsd-3528204[main] nfs_start_grace :STATE :EVENT :NFS Server Now IN GRACE, duration 90
09/04/2023 19:48:07 : epoch 6432fa56 : raspberry2 : ganesha.nfsd-3528204[main] load_fsal :NFS STARTUP :FATAL :Could not dlopen module: /usr/lib/aarch64-linux-gnu/ganesha/libfsalgluster.so Error: /lib/aarch64-linux-gnu/libtcmalloc_minimal.so.4: cannot allocate memory in static TLS block. You might want to install the nfs-ganesha-GLUSTER package
```

[I][B]systemctl status nfs-ganesha
[/B][/I]```
× nfs-ganesha.service - NFS-Ganesha file server
     Loaded: loaded (/lib/systemd/system/nfs-ganesha.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Sun 2023-04-09 19:48:07 CEST; 11min ago
       Docs: http://github.com/nfs-ganesha/nfs-ganesha/wiki
    Process: 3528203 ExecStart=/bin/bash -c ${NUMACTL} ${NUMAOPTS} /usr/bin/ganesha.nfsd ${OPTIONS} ${EPOCH} (code=exited, status=0/SUCCESS)
   Main PID: 3528204 (code=exited, status=2)
        CPU: 295ms


Apr 09 19:48:06 raspberry2 systemd[1]: Starting NFS-Ganesha file server...
Apr 09 19:48:06 raspberry2 systemd[1]: Started NFS-Ganesha file server.
Apr 09 19:48:07 raspberry2 systemd[1]: nfs-ganesha.service: Main process exited, code=exited, status=2/INVALIDARGUMENT
Apr 09 19:48:07 raspberry2 systemd[1]: nfs-ganesha.service: Failed with result 'exit-code'.


```

---

