---
title: "prob with my vi /etc/hosts installation steps"
date: 2006-07-20
forum: Installation &amp; Upgrades
---

### Post by alel on 2006-07-20
](*,)  Gosh..

I don't know how to make the value I insert become  the new setting. Can anyone help me

in vi /etc/hosts , I inserted the below value:

127.0.0.1       localhost.localdomain   localhost
xxx.xxx.xxx.xxx mylocalhost.mydomain    mylocalhost
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


after I done with editing the above value, I restart(reboot) but nothing still change and keep giving the default setting as follow:

127.0.0.1       localhost.localdomain localhost
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

And 1 stupid quetion](*,) ? how do I get out of the editing area? At the moment I just restart (ctrl+alt+del)..Is this the wrong way....Because it seems to work while I setup the static IP

---

### Post by MonkeyNet on 2006-07-20
From what you have written the problem is that you have not saved the file in vi

After inserting the values into the hosts file hit ESC.

Then proceed with the following keyboard command
:wq

This tells vi to write the file to disk and quit. Make sure you are editing the file as the root user, otherwise you will not be able to save it.

Cheers,

Andrew

---

### Post by alel on 2006-07-20
Thanks MonkeyNet.

I just barely know how to save....so naive...](*,) 

Thanks anyway....ure my lifesaver

---

### Post by alel on 2006-07-20
Hi,

Wasn't the 'hostname' and 'hostname -f' will result in the same value?

I got some problem when the 'hostname' show the value 'mandrak'
while
'hostname -f' show the value 'mandrak.lizret.com'

In the guide of server installation in this URL:
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3)

Both 'hostname' and 'hostname -f' should show the same result. After reboot for few time, the shown result is still the same.

This is my setting in 'vi /etc/hosts'

127.0.0.1       localhost.localdomain localhost
192.168.0.100   mandrak.lizret.com     mandrak

Can anybody please show me how to make both value same :confused:

---

