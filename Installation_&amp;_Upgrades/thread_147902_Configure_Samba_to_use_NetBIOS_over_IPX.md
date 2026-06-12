---
title: "Configure Samba to use NetBIOS over IPX"
date: 2006-03-21
forum: Installation &amp; Upgrades
---

### Post by two_clicks on 2006-03-21
My home network is setup with two protocols IPX and TCP/IP. In setting up Samba I found that the only way I could see the file share was to reconfigure the Windows PC to bind TCP/IP to File and Print Sharing (I normally operate with only IPX used for File and Priint Sharing) In researching the internet on the topic I found the following statement

"Nowadays, the Transport protocol used for NetBIOS is IP, or occasionally IPX. Applications such as SAMBA actually require NetBIOS to run over IP although some versions of SAMBA can run over IPX." 

Would like to ask the forum members if the version of Samba bundled with Ubuntu could be configued to use NetBios over IPX?

I did enable IPX but still could not see the file share. I am very very new to Linux and if a configuration is possible explicit directions would be greatly appreciated

---

### Post by localzuk on 2006-03-21
Hi,

Before I look into Samba, could you explain why you want to use IPX? It is an outdated protocol which should have died long ago.

---

### Post by localzuk on 2006-03-21
Now that I have looked into it, the problem is likely to be the use of 2 transport protocols on windows. Take a look at [http://us2.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html#id2551082](http://us2.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html#id2551082) which explains it better. :)

---

### Post by two_clicks on 2006-03-21
The decision to use two protocols was largely based upon the information given at [http://www.grc.com/su-rebinding9x.htm](http://www.grc.com/su-rebinding9x.htm) which advocates the isolation of tcp/ip from protocols that provide access to local/private files.

I never got the impression that having two protocols was the problem; when I bound tcp/ip to file and print sharing (which is linked to ipx/spx) the file shares were readily visble and accessible on the WinXP and Win95 machines and the Ubuntu machine saw all the file shares on both machines. 

I like the convenience of having all my files shares readily accessible without the need for logins or passwords that why I'm a staunch advocate of running file sharing on a protocol that is seperate from and not linked to tcp/ip

---

### Post by bergersau on 2006-03-22
Save yourself the pain - just use TCP/IP for everything and ensure your gateway is not listening on any ports you dont explicitly want/need open.

My 2c...

---

