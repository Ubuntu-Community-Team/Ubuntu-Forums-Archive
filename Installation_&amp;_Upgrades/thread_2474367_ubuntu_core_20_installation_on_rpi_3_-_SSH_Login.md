---
title: "ubuntu core 20 installation on rpi 3 - SSH Login"
date: 2022-04-27
forum: Installation &amp; Upgrades
---

### Post by manish9873 on 2022-04-27
I have installed new Ubuntu core 20 as per below Link.

[https://ubuntu.com/core/docs/uc20/install-raspberry-pi#heading--1](https://ubuntu.com/core/docs/uc20/install-raspberry-pi#heading--1)

Now, I'm unable to login on command line through Putty and SSH. They require a password for Login.

I also have tried user name=ubuntu and password=ubuntu but this is not working on console.

```
debug3: send packet: type 21
debug2: set_newkeys: mode 1
debug1: rekey after 134217728 blocks
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug3: receive packet: type 21
debug1: SSH2_MSG_NEWKEYS received
debug2: set_newkeys: mode 0
debug1: rekey after 134217728 blocks
debug2: key: /root/.ssh/id_rsa (0x147fed0)
debug2: key: /root/.ssh/id_dsa ((nil))
debug2: key: /root/.ssh/id_ecdsa ((nil))
debug2: key: /root/.ssh/id_ed25519 ((nil))
debug3: send packet: type 5
debug3: receive packet: type 7
debug1: SSH2_MSG_EXT_INFO received
debug1: kex_input_ext_info: server-sig-algs=<ssh-ed25519,sk-ssh-ed25519@openssh.com,ssh-rsa,rsa-sha2-256,rsa-sha2-512,ssh-dss,ecdsa-sha2-nistp256,ecdsa-sha2-nistp384,ecdsa-sha2-nistp521,sk-ecdsa-sha2-nistp256@openssh.com>
debug3: receive packet: type 6
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug3: send packet: type 50
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /root/.ssh/id_rsa
debug3: send_pubkey_test
debug3: send packet: type 50
debug2: we sent a publickey packet, wait for reply
debug3: receive packet: type 51
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /root/.ssh/id_dsa
debug3: no such identity: /root/.ssh/id_dsa: No such file or directory
debug1: Trying private key: /root/.ssh/id_ecdsa
debug3: no such identity: /root/.ssh/id_ecdsa: No such file or directory
debug1: Trying private key: /root/.ssh/id_ed25519
debug3: no such identity: /root/.ssh/id_ed25519: No such file or directory
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
manish9873@192.168.1.181's password:
```

I want to login on console for some setup on RPI3..

---

### Post by TheFu on 2022-04-28
I think Ubuntu Core requires using a Canonical IoT account for ssh authentication. Isn't it called Landscape or something like that?
Ubuntu Core is meant for IoT deployments, not as an end-user OS.  I truly hope they don't allow passwords to be used and mandate the use of ssh-keys.

For end users, they make Ubuntu Server ARM and Ubuntu Desktop ARM releases.  A r-pi v3 would struggle to run the normal Ubuntu Desktop, so look for a lighter one - perhaps Mate or XFCE instead of Gnome or Unity.

But I really don't know. In my reading of Ubuntu Core, it was clear that the mandated connection to Canonical wasn't something I wanted.

---

### Post by ActionParsnip on 2022-04-28
What command / settings are you trying to use to connect? Looks like you are using the username "root", is this right?

---

### Post by TheFu on 2022-04-28
[https://ubuntu.com/download/raspberry-pi-core](https://ubuntu.com/download/raspberry-pi-core) has step 1 as:
> 1. Set up an Ubuntu SSO account - _**An Ubuntu SSO account is required to create the first user on an Ubuntu Core installation**_.

....  more steps

> This device is registered to <Ubuntu SSO email address>.
Remote access was enabled via authentication with the SSO user <Ubuntu SSO user name>
Public SSH keys were added to the device for remote access.


.... more steps ....

> Step X Login - Once setup is done, you can login with SSH into Ubuntu Core, from a machine on the same network, using the following command:
```
$ ssh <Ubuntu SSO user name>@<device IP address>
```
Your user name is your Ubuntu SSO user name, it has been reminded to you at the end of the account configuration step.

So - use the Ubuntu SSO login.

---

