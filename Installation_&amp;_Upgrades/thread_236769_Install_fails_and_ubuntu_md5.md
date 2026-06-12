---
title: "Install fails and ubuntu md5?"
date: 2006-08-15
forum: Installation &amp; Upgrades
---

### Post by helmutvandeshaft on 2006-08-15
Hi All

I am having a slight problem installing Dapper Drake on an Intel system.

Both the server install and the desktop install are failing when certain files are being installed.

I thought maybe the download had been corrupt so I downloaded some Ubuntu MD5SUMS from different servers and diff'ed them. 

The result:

$ diff 1MD5SUMS.txt MD5SUMS.txt
1,10c1,10
< df03811bfc9f2a73672887a36d531965  ubuntu-6.06-alternate-amd64.iso
< b2e9120f06d70cc076c1852c6c04654e  ubuntu-6.06-alternate-i386.iso
< 12bd53a48d7afbcfb0eae6794a1ac02f  ubuntu-6.06-alternate-powerpc.iso
< 722b8b4a75f977a76a722d4a2b071b19  ubuntu-6.06-desktop-amd64.iso
< e2e5e0bfb2edffd2ce02dd77bda4558e  ubuntu-6.06-desktop-i386.iso
< 410d766d75a3afaa7f04c0c7dbdfd8da  ubuntu-6.06-desktop-powerpc.iso
< 02772b8b3461c246a2154aa6e699335b  ubuntu-6.06-server-amd64.iso
< 4c7c835d244453b9a29d397e5cd973fd  ubuntu-6.06-server-i386.iso
< c1f9c3dc78572bc2ce76d44776949fcc  ubuntu-6.06-server-powerpc.iso
< 82da246064785adb7b87e5aa0cb5764c  ubuntu-6.06-server-sparc.iso
---
 > b9a5be3a5858ade278d664d41310a4ab  ubuntu-6.06.1-alternate-amd64.iso
 > 6cb8582aa5615ed4616165743a0868d7  ubuntu-6.06.1-alternate-i386.iso
 > 0b5b3df02da3d9ed6f4ac482cf541f04  ubuntu-6.06.1-alternate-powerpc.iso
 > 50e3912c555f98f7bca56b2a0200b205  ubuntu-6.06.1-desktop-amd64.iso
 > fb3af44c21f1f68cc25fda7edb8c1bd3  ubuntu-6.06.1-desktop-i386.iso
 > 502911770ad173dbe82c698379ed7d11  ubuntu-6.06.1-desktop-powerpc.iso
 > 8254b0f3696ed17c52a2cb59c9ebd2cc  ubuntu-6.06.1-server-amd64.iso
 > 5ad76d8b380ab5be713e5daa9ea84475  ubuntu-6.06.1-server-i386.iso
 > 6d1c3b5cb41661365b3db5cf12bb2836  ubuntu-6.06.1-server-powerpc.iso
 > 7ea4d7b75921e52c50ccb382ee0f7d7c  ubuntu-6.06.1-server-sparc.iso

diff MD5SUMS-aus.txt MD5SUMS-nl.txt
1,10c1,10
< df03811bfc9f2a73672887a36d531965  ubuntu-6.06-alternate-amd64.iso
< b2e9120f06d70cc076c1852c6c04654e  ubuntu-6.06-alternate-i386.iso
< 12bd53a48d7afbcfb0eae6794a1ac02f  ubuntu-6.06-alternate-powerpc.iso
< 722b8b4a75f977a76a722d4a2b071b19  ubuntu-6.06-desktop-amd64.iso
< e2e5e0bfb2edffd2ce02dd77bda4558e  ubuntu-6.06-desktop-i386.iso
< 410d766d75a3afaa7f04c0c7dbdfd8da  ubuntu-6.06-desktop-powerpc.iso
< 02772b8b3461c246a2154aa6e699335b  ubuntu-6.06-server-amd64.iso
< 4c7c835d244453b9a29d397e5cd973fd  ubuntu-6.06-server-i386.iso
< c1f9c3dc78572bc2ce76d44776949fcc  ubuntu-6.06-server-powerpc.iso
< 82da246064785adb7b87e5aa0cb5764c  ubuntu-6.06-server-sparc.iso
---
 > b9a5be3a5858ade278d664d41310a4ab  ubuntu-6.06.1-alternate-amd64.iso
 > 6cb8582aa5615ed4616165743a0868d7  ubuntu-6.06.1-alternate-i386.iso
 > 0b5b3df02da3d9ed6f4ac482cf541f04  ubuntu-6.06.1-alternate-powerpc.iso
 > 50e3912c555f98f7bca56b2a0200b205  ubuntu-6.06.1-desktop-amd64.iso
 > fb3af44c21f1f68cc25fda7edb8c1bd3  ubuntu-6.06.1-desktop-i386.iso
 > 502911770ad173dbe82c698379ed7d11  ubuntu-6.06.1-desktop-powerpc.iso
 > 8254b0f3696ed17c52a2cb59c9ebd2cc  ubuntu-6.06.1-server-amd64.iso
 > 5ad76d8b380ab5be713e5daa9ea84475  ubuntu-6.06.1-server-i386.iso
 > 6d1c3b5cb41661365b3db5cf12bb2836  ubuntu-6.06.1-server-powerpc.iso
 > 7ea4d7b75921e52c50ccb382ee0f7d7c  ubuntu-6.06.1-server-sparc.iso

 diff MD5SUMS-uk.txt MD5SUMS-nl.txt
 diff MD5SUMS-us.txt MD5SUMS-nl.txt
 diff MD5SUMS-fr.txt MD5SUMS-nl.txt

1,10c1,10
< df03811bfc9f2a73672887a36d531965  ubuntu-6.06-alternate-amd64.iso
< b2e9120f06d70cc076c1852c6c04654e  ubuntu-6.06-alternate-i386.iso
< 12bd53a48d7afbcfb0eae6794a1ac02f  ubuntu-6.06-alternate-powerpc.iso
< 722b8b4a75f977a76a722d4a2b071b19  ubuntu-6.06-desktop-amd64.iso
< e2e5e0bfb2edffd2ce02dd77bda4558e  ubuntu-6.06-desktop-i386.iso
< 410d766d75a3afaa7f04c0c7dbdfd8da  ubuntu-6.06-desktop-powerpc.iso
< 02772b8b3461c246a2154aa6e699335b  ubuntu-6.06-server-amd64.iso
< 4c7c835d244453b9a29d397e5cd973fd  ubuntu-6.06-server-i386.iso
< c1f9c3dc78572bc2ce76d44776949fcc  ubuntu-6.06-server-powerpc.iso
< 82da246064785adb7b87e5aa0cb5764c  ubuntu-6.06-server-sparc.iso
---
 > b9a5be3a5858ade278d664d41310a4ab  ubuntu-6.06.1-alternate-amd64.iso
 > 6cb8582aa5615ed4616165743a0868d7  ubuntu-6.06.1-alternate-i386.iso
 > 0b5b3df02da3d9ed6f4ac482cf541f04  ubuntu-6.06.1-alternate-powerpc.iso
 > 50e3912c555f98f7bca56b2a0200b205  ubuntu-6.06.1-desktop-amd64.iso
 > fb3af44c21f1f68cc25fda7edb8c1bd3  ubuntu-6.06.1-desktop-i386.iso
 > 502911770ad173dbe82c698379ed7d11  ubuntu-6.06.1-desktop-powerpc.iso
 > 8254b0f3696ed17c52a2cb59c9ebd2cc  ubuntu-6.06.1-server-amd64.iso
 > 5ad76d8b380ab5be713e5daa9ea84475  ubuntu-6.06.1-server-i386.iso
 > 6d1c3b5cb41661365b3db5cf12bb2836  ubuntu-6.06.1-server-powerpc.iso
 > 7ea4d7b75921e52c50ccb382ee0f7d7c  ubuntu-6.06.1-server-sparc.iso
diff MD5SUMS-aus.txt MD5SUMS-fr.txt


Looks like the Australian one differs from the Dutch, English and US  
one but is the same as the French one.
Corrupt distribution?

Thanks

---

