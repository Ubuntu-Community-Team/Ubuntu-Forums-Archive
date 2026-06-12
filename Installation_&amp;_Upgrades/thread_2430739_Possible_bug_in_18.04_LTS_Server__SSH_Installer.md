---
title: "Possible bug in 18.04 LTS Server / SSH Installer?"
date: 2019-11-06
forum: Installation &amp; Upgrades
---

### Post by geskalney on 2019-11-06
I'm not sure if this is a bug or not, but I've never run into this before over the last ten years or so... (and my google-fu has failed to find a cause/solution/similar issue)
When you install Open SSH Server, the user account you created when installing the operating system isn't allowed to log in over SSH.
You can log in locally, any user that you create after the OS is up an running can log in remotely, but the original user can't.
Changing the first user's password doesn't fix it. I've tried installing SSH with the server install, I've tried installing it after the fact. I've tried updating the whole system to the current apt state before installing ssh, no luck.
I've tried the LIVE iso and the classic iso.
Is it because I'm installing the servers as VMs in QEMU?
Is it because I'm using LVM?
Extra weird... Doesn't always happen. I have installed five VMs today, all exhibit the same behavior, I just did a test now, didn't use LVM, i can SSH in remotely. Is that it? Is LVM somehow (I can't imagine how) causing this?

---

### Post by Skaperen on 2019-11-06
that could be a change in the default security setting to prevent the administrator from logging in from remote locations like the internet.  i would guess that it can be changed.  i have never done this, so i don't know what to change.  my install user is "admini" and is the backup administrator account.  i then created the users i need to use.  so, i have not had any need to change this.  i'm glad that the user allowed to use [COLOR=#0000cd][FONT=courier new]**sudo**[/FONT][/COLOR] cannot login from the internet.  what is your feeling on that?

---

### Post by TheFu on 2019-11-06
I have a test 18.04 server.  It uses LVM for storage management by the host.  The LV is provided as a block device to the guest.  I'm using KVM/QEMU.  No issues at all with ssh.  The account used to install the server works fine with ssh.
I use the password, just once when I use ssh-copy-id to push over public keys from clients.  After that, almost exclusively ssh with keys will be used.

I always select to install the ssh-server during installs - server or desktop.

Does **ssh -vvvv** show anything bad?

Which networking do the VMs use?  The built-in NAT or did you manually setup a Linux bridge using bridge-utils?

---

### Post by geskalney on 2019-11-07
My guess is that the first user account isn't getting synced to ssh, it's "not found":

```
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /Users/user/.ssh/id_dsa
debug3: no such identity: /Users/user/.ssh/id_dsa: No such file or directory
debug1: Trying private key: /Users/user/.ssh/id_ecdsa
debug3: no such identity: /Users/user/.ssh/id_ecdsa: No such file or directory
debug1: Trying private key: /Users/user/.ssh/id_ed25519
debug3: no such identity: /Users/user/.ssh/id_ed25519: No such file or directory
debug1: Trying private key: /Users/user/.ssh/id_xmss
debug3: no such identity: /Users/user/.ssh/id_xmss: No such file or directory
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
user@0.0.0.0's password: 
debug3: send packet: type 50
debug2: we sent a password packet, wait for reply
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.

```

The VMs are using a QEMU network bridge. (I have no problem accessing them over the network)

I have no personal problem with sudo accounts having network access, it's all behind a firewall; plus it would be immensely inconvenient to have to go to the actual box any time I have to sudo something.

I'm looking for a way to change the setting (it's probably more restrictive security introduced in 18), but I'm working around it by creating accounts after the install which have no problem ssh'ing in over the network.

---

### Post by TheFu on 2019-11-07
Rather than describing what you believe, can you please run commands and show both those and the output to prove each?  Always show the exact command used, not just the output, otherwise we don't have any hope of understanding what we are seeing.

Be certain to include the output from **ls -la ~user/.ssh/** for the user.

---

### Post by geskalney on 2019-11-07
Fail:

```
SYS:~ nuser$ ssh -vvvv nuser@10.0.100.100OpenSSH_7.8p1, LibreSSL 2.6.2
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 48: Applying options for *
debug2: resolve_canonicalize: hostname 10.0.100.100 is address
debug2: ssh_connect_direct
debug1: Connecting to 10.0.100.100 [10.0.100.100] port 22.
debug1: Connection established.
debug1: identity file /Users/nuser/.ssh/id_rsa type 0
debug1: identity file /Users/nuser/.ssh/id_rsa-cert type -1
debug1: identity file /Users/nuser/.ssh/id_dsa type -1
debug1: identity file /Users/nuser/.ssh/id_dsa-cert type -1
debug1: identity file /Users/nuser/.ssh/id_ecdsa type -1
debug1: identity file /Users/nuser/.ssh/id_ecdsa-cert type -1
debug1: identity file /Users/nuser/.ssh/id_ed25519 type -1
debug1: identity file /Users/nuser/.ssh/id_ed25519-cert type -1
debug1: identity file /Users/nuser/.ssh/id_xmss type -1
debug1: identity file /Users/nuser/.ssh/id_xmss-cert type -1
debug1: Local version string SSH-2.0-OpenSSH_7.8
debug1: Remote protocol version 2.0, remote software version OpenSSH_7.6p1 Ubuntu-4ubuntu0.3
debug1: match: OpenSSH_7.6p1 Ubuntu-4ubuntu0.3 pat OpenSSH_7.0*,OpenSSH_7.1*,OpenSSH_7.2*,OpenSSH_7.3*,OpenSSH_7.4*,OpenSSH_7.5*,OpenSSH_7.6*,OpenSSH_7.7* compat 0x04000002
debug2: fd 3 setting O_NONBLOCK
debug1: Authenticating to 10.0.100.100:22 as 'nuser'
debug3: hostkeys_foreach: reading file "/Users/nuser/.ssh/known_hosts"
debug3: record_hostkey: found key type ECDSA in file /Users/nuser/.ssh/known_hosts:35
debug3: load_hostkeys: loaded 1 keys from 10.0.100.100
debug3: order_hostkeyalgs: prefer hostkeyalgs: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521
debug3: send packet: type 20
debug1: SSH2_MSG_KEXINIT sent
debug3: receive packet: type 20
debug1: SSH2_MSG_KEXINIT received
debug2: local client KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group14-sha256,diffie-hellman-group14-sha1,ext-info-c
debug2: host key algorithms: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-ed25519-cert-v01@openssh.com,rsa-sha2-512-cert-v01@openssh.com,rsa-sha2-256-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ssh-ed25519,rsa-sha2-512,rsa-sha2-256,ssh-rsa
debug2: ciphers ctos: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: ciphers stoc: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: MACs ctos: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com,zlib
debug2: compression stoc: none,zlib@openssh.com,zlib
debug2: languages ctos: 
debug2: languages stoc: 
debug2: first_kex_follows 0 
debug2: reserved 0 
debug2: peer server KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group14-sha256,diffie-hellman-group14-sha1
debug2: host key algorithms: ssh-rsa,rsa-sha2-512,rsa-sha2-256,ecdsa-sha2-nistp256,ssh-ed25519
debug2: ciphers ctos: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: ciphers stoc: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: MACs ctos: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com
debug2: compression stoc: none,zlib@openssh.com
debug2: languages ctos: 
debug2: languages stoc: 
debug2: first_kex_follows 0 
debug2: reserved 0 
debug1: kex: algorithm: curve25519-sha256
debug1: kex: host key algorithm: ecdsa-sha2-nistp256
debug1: kex: server->client cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug1: kex: client->server cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug3: send packet: type 30
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug3: receive packet: type 31
debug1: Server host key: ecdsa-sha2-nistp256 SHA256:h3M4begTlRZOzrpSI096dms7saHQhRK7dG5Vuu06FVU
debug3: hostkeys_foreach: reading file "/Users/nuser/.ssh/known_hosts"
debug3: record_hostkey: found key type ECDSA in file /Users/nuser/.ssh/known_hosts:35
debug3: load_hostkeys: loaded 1 keys from 10.0.100.100
debug1: Host '10.0.100.100' is known and matches the ECDSA host key.
debug1: Found key in /Users/nuser/.ssh/known_hosts:35
debug3: send packet: type 21
debug2: set_newkeys: mode 1
debug1: rekey after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug3: receive packet: type 21
debug1: SSH2_MSG_NEWKEYS received
debug2: set_newkeys: mode 0
debug1: rekey after 134217728 blocks
debug2: key: /Users/nuser/.ssh/id_rsa (0x7fd4c7c0f840)
debug2: key: /Users/nuser/.ssh/id_dsa (0x0)
debug2: key: /Users/nuser/.ssh/id_ecdsa (0x0)
debug2: key: /Users/nuser/.ssh/id_ed25519 (0x0)
debug2: key: /Users/nuser/.ssh/id_xmss (0x0)
debug3: send packet: type 5
debug3: receive packet: type 7
debug1: SSH2_MSG_EXT_INFO received
debug1: kex_input_ext_info: server-sig-algs=<ssh-ed25519,ssh-rsa,rsa-sha2-256,rsa-sha2-512,ssh-dss,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521>
debug3: receive packet: type 6
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug3: send packet: type 50
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering public key: RSA SHA256:T/dfiVm3Wj1FTyLdBn4QR1a3rhNBvdTjwy+/cSJBq4o /Users/nuser/.ssh/id_rsa
debug3: send packet: type 50
debug2: we sent a publickey packet, wait for reply
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /Users/nuser/.ssh/id_dsa
debug3: no such identity: /Users/nuser/.ssh/id_dsa: No such file or directory
debug1: Trying private key: /Users/nuser/.ssh/id_ecdsa
debug3: no such identity: /Users/nuser/.ssh/id_ecdsa: No such file or directory
debug1: Trying private key: /Users/nuser/.ssh/id_ed25519
debug3: no such identity: /Users/nuser/.ssh/id_ed25519: No such file or directory
debug1: Trying private key: /Users/nuser/.ssh/id_xmss
debug3: no such identity: /Users/nuser/.ssh/id_xmss: No such file or directory
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
nuser@10.0.100.100's password: 
debug3: send packet: type 50
debug2: we sent a password packet, wait for reply
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
nuser@10.0.100.100's password: 
debug3: send packet: type 50
debug2: we sent a password packet, wait for reply
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
nuser@10.0.100.100's password: 
debug3: send packet: type 50
debug2: we sent a password packet, wait for reply
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey,password
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
nuser@10.0.100.100: Permission denied (publickey,password).
SYS:~ nuser$ 



```

Success:

```


Last login: Thu Nov  7 09:28:22 on ttys000
SYS:~ nuser$ ssh -vvvv luser@10.0.100.101
OpenSSH_7.8p1, LibreSSL 2.6.2
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 48: Applying options for *
debug2: resolve_canonicalize: hostname 10.0.100.101 is address
debug2: ssh_connect_direct
debug1: Connecting to 10.0.100.101 [10.0.100.101] port 22.
debug1: Connection established.
debug1: identity file /Users/nuser/.ssh/id_rsa type 0
debug1: identity file /Users/nuser/.ssh/id_rsa-cert type -1
debug1: identity file /Users/nuser/.ssh/id_dsa type -1
debug1: identity file /Users/nuser/.ssh/id_dsa-cert type -1
debug1: identity file /Users/nuser/.ssh/id_ecdsa type -1
debug1: identity file /Users/nuser/.ssh/id_ecdsa-cert type -1
debug1: identity file /Users/nuser/.ssh/id_ed25519 type -1
debug1: identity file /Users/nuser/.ssh/id_ed25519-cert type -1
debug1: identity file /Users/nuser/.ssh/id_xmss type -1
debug1: identity file /Users/nuser/.ssh/id_xmss-cert type -1
debug1: Local version string SSH-2.0-OpenSSH_7.8
debug1: Remote protocol version 2.0, remote software version OpenSSH_7.6p1 Ubuntu-4ubuntu0.3
debug1: match: OpenSSH_7.6p1 Ubuntu-4ubuntu0.3 pat OpenSSH_7.0*,OpenSSH_7.1*,OpenSSH_7.2*,OpenSSH_7.3*,OpenSSH_7.4*,OpenSSH_7.5*,OpenSSH_7.6*,OpenSSH_7.7* compat 0x04000002
debug2: fd 3 setting O_NONBLOCK
debug1: Authenticating to 10.0.100.101:22 as 'luser'
debug3: hostkeys_foreach: reading file "/Users/nuser/.ssh/known_hosts"
debug3: record_hostkey: found key type ECDSA in file /Users/nuser/.ssh/known_hosts:36
debug3: load_hostkeys: loaded 1 keys from 10.0.100.101
debug3: order_hostkeyalgs: prefer hostkeyalgs: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521
debug3: send packet: type 20
debug1: SSH2_MSG_KEXINIT sent
debug3: receive packet: type 20
debug1: SSH2_MSG_KEXINIT received
debug2: local client KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group14-sha256,diffie-hellman-group14-sha1,ext-info-c
debug2: host key algorithms: ecdsa-sha2-nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,ssh-ed25519-cert-v01@openssh.com,rsa-sha2-512-cert-v01@openssh.com,rsa-sha2-256-cert-v01@openssh.com,ssh-rsa-cert-v01@openssh.com,ssh-ed25519,rsa-sha2-512,rsa-sha2-256,ssh-rsa
debug2: ciphers ctos: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: ciphers stoc: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: MACs ctos: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com,zlib
debug2: compression stoc: none,zlib@openssh.com,zlib
debug2: languages ctos: 
debug2: languages stoc: 
debug2: first_kex_follows 0 
debug2: reserved 0 
debug2: peer server KEXINIT proposal
debug2: KEX algorithms: curve25519-sha256,curve25519-sha256@libssh.org,ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-group-exchange-sha256,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group14-sha256,diffie-hellman-group14-sha1
debug2: host key algorithms: ssh-rsa,rsa-sha2-512,rsa-sha2-256,ecdsa-sha2-nistp256,ssh-ed25519
debug2: ciphers ctos: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: ciphers stoc: chacha20-poly1305@openssh.com,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com
debug2: MACs ctos: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: MACs stoc: umac-64-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-256-etm@openssh.com,hmac-sha2-512-etm@openssh.com,hmac-sha1-etm@openssh.com,umac-64@openssh.com,umac-128@openssh.com,hmac-sha2-256,hmac-sha2-512,hmac-sha1
debug2: compression ctos: none,zlib@openssh.com
debug2: compression stoc: none,zlib@openssh.com
debug2: languages ctos: 
debug2: languages stoc: 
debug2: first_kex_follows 0 
debug2: reserved 0 
debug1: kex: algorithm: curve25519-sha256
debug1: kex: host key algorithm: ecdsa-sha2-nistp256
debug1: kex: server->client cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug1: kex: client->server cipher: chacha20-poly1305@openssh.com MAC: <implicit> compression: none
debug3: send packet: type 30
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug3: receive packet: type 31
debug1: Server host key: ecdsa-sha2-nistp256 SHA256:FbQBrMnAEWP81F5/cQtyWSPIQOSllKaCAXyzY0pwhLs
debug3: hostkeys_foreach: reading file "/Users/nuser/.ssh/known_hosts"
debug3: record_hostkey: found key type ECDSA in file /Users/nuser/.ssh/known_hosts:36
debug3: load_hostkeys: loaded 1 keys from 10.0.100.101
debug1: Host '10.0.100.101' is known and matches the ECDSA host key.
debug1: Found key in /Users/nuser/.ssh/known_hosts:36
debug3: send packet: type 21
debug2: set_newkeys: mode 1
debug1: rekey after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug3: receive packet: type 21
debug1: SSH2_MSG_NEWKEYS received
debug2: set_newkeys: mode 0
debug1: rekey after 134217728 blocks
debug2: key: /Users/nuser/.ssh/id_rsa (0x7fa3b9c1ad30)
debug2: key: /Users/nuser/.ssh/id_dsa (0x0)
debug2: key: /Users/nuser/.ssh/id_ecdsa (0x0)
debug2: key: /Users/nuser/.ssh/id_ed25519 (0x0)
debug2: key: /Users/nuser/.ssh/id_xmss (0x0)
debug3: send packet: type 5
debug3: receive packet: type 7
debug1: SSH2_MSG_EXT_INFO received
debug1: kex_input_ext_info: server-sig-algs=<ssh-ed25519,ssh-rsa,rsa-sha2-256,rsa-sha2-512,ssh-dss,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521>
debug3: receive packet: type 6
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug3: send packet: type 50
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering public key: RSA SHA256:T/dfiVm3Wj1FTyLdBn4QR1a3yhNBvdTjwy+/cSJBq4o /Users/nuser/.ssh/id_rsa
debug3: send packet: type 50
debug2: we sent a publickey packet, wait for reply
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /Users/nuser/.ssh/id_dsa
debug3: no such identity: /Users/nuser/.ssh/id_dsa: No such file or directory
debug1: Trying private key: /Users/nuser/.ssh/id_ecdsa
debug3: no such identity: /Users/nuser/.ssh/id_ecdsa: No such file or directory
debug1: Trying private key: /Users/nuser/.ssh/id_ed25519
debug3: no such identity: /Users/nuser/.ssh/id_ed25519: No such file or directory
debug1: Trying private key: /Users/nuser/.ssh/id_xmss
debug3: no such identity: /Users/nuser/.ssh/id_xmss: No such file or directory
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
luser@10.0.100.101's password: 
debug3: send packet: type 50
debug2: we sent a password packet, wait for reply
debug3: receive packet: type 52
debug1: Authentication succeeded (password).
Authenticated to 10.0.100.101 ([10.0.100.101]:22).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug3: send packet: type 90
debug1: Requesting no-more-sessions@openssh.com
debug3: send packet: type 80
debug1: Entering interactive session.
debug1: pledge: network
debug3: receive packet: type 80
debug1: client_input_global_request: rtype hostkeys-00@openssh.com want_reply 0
debug3: receive packet: type 91
debug2: channel_input_open_confirmation: channel 0: callback start
debug2: fd 3 setting TCP_NODELAY
debug3: ssh_packet_set_tos: set IP_TOS 0x48
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 1
debug3: send packet: type 98
debug1: Sending environment.
debug3: Ignored env TERM_PROGRAM
debug3: Ignored env SHELL
debug3: Ignored env TERM
debug3: Ignored env TMPDIR
debug3: Ignored env Apple_PubSub_Socket_Render
debug3: Ignored env TERM_PROGRAM_VERSION
debug3: Ignored env TERM_SESSION_ID
debug3: Ignored env USER
debug3: Ignored env SSH_AUTH_SOCK
debug3: Ignored env PATH
debug3: Ignored env PWD
debug1: Sending env LANG = en_CA.UTF-8
debug2: channel 0: request env confirm 0
debug3: send packet: type 98
debug3: Ignored env XPC_FLAGS
debug3: Ignored env XPC_SERVICE_NAME
debug3: Ignored env SHLVL
debug3: Ignored env HOME
debug3: Ignored env LOGNAME
debug3: Ignored env _
debug3: Ignored env __CF_USER_TEXT_ENCODING
debug2: channel 0: request shell confirm 1
debug3: send packet: type 98
debug2: channel_input_open_confirmation: channel 0: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug3: receive packet: type 99
debug2: channel_input_status_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 2097152
debug3: receive packet: type 99
debug2: channel_input_status_confirm: type 99 id 0
debug2: shell request accepted on channel 0
Welcome to Ubuntu 18.04.3 LTS (GNU/Linux 4.15.0-55-generic x86_64)


 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage


  System information as of Thu Nov  7 10:43:44 EST 2019


  System load:  0.0                Processes:           112
  Usage of /:   13.1% of 13.76GB   Users logged in:     1
  Memory usage: 7%                 IP address for ens3: 10.0.100.101
  Swap usage:   0%




85 packages can be updated.
41 updates are security updates.




Last login: Thu Nov  7 10:42:30 2019 from 10.0.100.200
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.


luser@ubuntu:~$ 

```


In either case, there is not .ssh folder in the user folder.


```

total 32
drwxr-xr-x 4 nuser nuser 4096 Nov  6 13:15 .
drwxr-xr-x 5 root   root   4096 Nov  6 13:06 ..
-rw------- 1  nuser nuser  281 Nov  6 13:18 .bash_history
-rw-r--r-- 1  nuser nuser  220 Nov  6 12:56 .bash_logout
-rw-r--r-- 1  nuser nuser  3771 Nov  6 12:56 .bashrc
drwx------ 2  nuser nuser  4096 Nov  6 12:58 .cache
drwx------ 3  nuser nuser  4096 Nov  6 12:58 .gnupg
-rw-r--r-- 1  nuser nuser  807 Nov  6 12:56 .profile
-rw-r--r-- 1  nuser nuser   0 Nov  6 12:58 .sudo_as_admin_successful



```

---

### Post by TheFu on 2019-11-07
```
debug3: record_hostkey: found key type ECDSA in file /Users/nuser/.ssh/known_hosts:36
```
Uh ... what is this?

---

### Post by geskalney on 2019-11-07
That's local.

---

### Post by TheFu on 2019-11-07
I compared the working and non-working outputs using sdiff.  This might help:
```
debug1: Next authentication method: password                    debug1: Next authentication method: password
nuser@10.0.100.100's password:                                | luser@10.0.100.101's password: 
debug3: send packet: type 50                                    debug3: send packet: type 50
debug2: we sent a password packet, wait for reply               debug2: we sent a password packet, wait for reply
debug3: receive packet: type 51                               | debug3: receive packet: type 52
debug1: Authentications that can continue: publickey,password | debug1: Authentication succeeded (password).
Permission denied, please try again.                          | Authenticated to 10.0.100.101 ([10.0.100.101]:22).

```

Seems that file+directory permissions with ~/.ssh/ are usually the problem for this sort of issue.  The fact that it works with 1 login and not the other would have me thinking it was on the server-side.  It has been over a day.  I'd wipe all the ~/.ssh/ directories completely, create new keys, use ssh-copy-id to push them over and be done with it.

---

