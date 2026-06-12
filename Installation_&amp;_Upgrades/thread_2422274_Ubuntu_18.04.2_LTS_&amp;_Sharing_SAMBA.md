---
title: "Ubuntu 18.04.2 LTS &amp; Sharing SAMBA"
date: 2019-07-04
forum: Installation &amp; Upgrades
---

### Post by druidctba on 2019-07-04
Personally after installing Virtual Box on my Windows 10 Enterprise, I can no longer access through my media player DUNE HD SOLO LITE 4K the shared folders of it, it happens that the other media server that I have the NVIDIA SHIELD TV PRO 4K accesses without problems , I tried everything but I believe that the SMB protocol used by DUNE is poorly programmed, so I had the idea to install Ubuntu 18.04.2 LTS via PENDRIVER to create the shares that I need and everything was fine.

In Ubuntu when trying to share one of the folders that is on my Desktop (one of the folders already shared in Windows 10 Enterprise), it says that SAMBA is not installed (sharing service is not installed) and asks if I want to install, and I click on install and here comes the following problem:

failed to download files from packages

please check your internet connection

/samba_4.7.6+dfsg~ubuntu-0ubuntu2.6_amd64.deb 404 Not Found [IP: 2001: 67c: 1560: 8001 :: 11 80]
Failed to fetch [IP: 2001: 67c: 1560: 8001 :: 11] 80]
Failed to fetch [IP: 2001: 67c: 1560: 8001 :: 11] 80]
Failed to fetch [http://en.wikipedia.org/w/index.php?title=Category:Flags:](http://en.wikipedia.org/w/index.php?title=Category:Flags:) 1560: 8001 :: 11 80]
Failed to fetch [http://en.wikipedia.org/w/index.php?title=Flag_of_the_Bolt_of_the_Bolt](http://en.wikipedia.org/w/index.php?title=Flag_of_the_Bolt_of_the_Bolt) 1560: 8001 :: 11 80]

The internet is working perfectly, so much that I enter the browser and type a search and it finds the searched sites and I can navigate in them, then Internet connection is not, or does Linux work differently?

I installed Ubuntu on a 4Gigas SanDisk PENDRIVER, following instructions from this site: [https://zillowtech.com/ubuntu-bootable-usb.html/](https://zillowtech.com/ubuntu-bootable-usb.html/)

Can someone help me solve this problem :).

I thought SAMBA was native to the LINUX platform so much that because it is GNU it is used in most of the electronic equipment we find in the market, as in the case of my DUNE and NVIDIA mediaplayers.

Oh yes, DUNE also supports NFS sharing, even the company recommends it to be faster (but it is only available on NAS devices), it has an easy way to create a SAMBA and other NFS service on my UBUNTU 18.04.2 LTS?

Att.

Druid®.

-----------------------------------------------------------------------------------------------------------------------


Pessoal depois que instalei o Virtual Box no meu Windows 10 Enterprise, não mais consigo acessar pelo meu media player DUNE HD SOLO LITE 4K as pastas compartilhadas do mesmo, ocorre que o outro media server que eu tenho o NVIDIA SHIELD TV PRO 4K acessa sem problemas, já tentei de tudo, mas acredito que o protocolo SMB usado pelo DUNE seja bem mal programado, enfim ai tive a ideia de instalar o Ubuntu 18.04.2 LTS via PENDRIVER para criar os compartilhamentos que necessito e rodou tudo muito bem a instalação.

No Ubuntu ao tentar compartilhar para testes uma das pastas que está no meu Desktop (uma das pastas já compartilhadas no Windows 10 Enterprise), ele diz que o SAMBA não está instalado (serviço de compartilhamento não está instalado) e pergunta se eu desejo instalar, e clico em instalar e ai vem o seguinte problema:

falha ao baixar arquivos dos pacotes

favor verificar sua conexao com a internet

/samba_4.7.6+dfsg~ubuntu-0ubuntu2.6_amd64.deb 404  Not Found [IP: 2001:67c:1560:8001::11 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/ceph/librados2_12.2.8-0ubuntu0.18.04.2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/ceph/librados2_12.2.8-0ubuntu0.18.04.2_amd64.deb) 404  Not Found [IP: 2001:67c:1560:8001::11 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/ceph/libcephfs2_12.2.8-0ubuntu0.18.04.2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/ceph/libcephfs2_12.2.8-0ubuntu0.18.04.2_amd64.deb) 404  Not Found [IP: 2001:67c:1560:8001::11 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-dsdb-modules_4.7.6+dfsg~ubuntu-0ubuntu2.6_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-dsdb-modules_4.7.6+dfsg~ubuntu-0ubuntu2.6_amd64.deb) 404  Not Found [IP: 2001:67c:1560:8001::11 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-vfs-modules_4.7.6+dfsg~ubuntu-0ubuntu2.6_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-vfs-modules_4.7.6+dfsg~ubuntu-0ubuntu2.6_amd64.deb) 404  Not Found [IP: 2001:67c:1560:8001::11 80]

A internet está funcionando perfeitamente, tanto que entro no browser e digito uma pesquisa e ele encontra os sites pesquisados e posso navegar neles, então conexão com internet não é, ou o Linux funciona de maneira diferente?

Eu instalei o Ubuntu num PENDRIVER de 4Gigas SanDisk, seguindo instruções deste site: [https://zillowtech.com/ubuntu-bootable-usb.html/](https://zillowtech.com/ubuntu-bootable-usb.html/)
Alguém pode me ajudar a resolver este problema :).

Eu pensei que o SAMBA fosse nativo da plataforma LINUX tanto que por ser GNU é usado na maioria dos equipamentos eletrônicos que encontramos no mercado, como o caso dos meus mediaplayers DUNE e NVIDIA.

Ah sim, o DUNE também aceita compartilhamento NFS, incluse a empresa até recomenda seu uso por ser mais rápido (mas ele só está disponível nos equipamentos NAS), tem uma maneira fácil de criar um servido SAMBA e outro NFS no meu UBUNTU 18.04.2 LTS?

Att.

Druid®.

---

### Post by houstonbofh on 2019-07-04
You have a few different problems in your post.

1) Installs do not work.

2) You can not install SAMBA.

3) Is NFS better than Samba, and how do I install it?

Let me skip 1) for a second...

2) Yes, because installs are broken.  And very little file sharing is installed by default.  If it all was, the install would be huge!

3) I prefer NFS to samba, and it is easy to install.  But it is poorly supported in network manager so you will have to spend time in the cli to set it up.

Now back to 1)...

I noticed you are using IPv6 addresses, but that does not always resolve or transit correctly.  To start, try changing your update servers.  Also try running "sudo apt-get update" in a cli to get better error reporting.  I suspect it is all based on apt not being able to communicate withe the update servers.

---

### Post by george-bungarzescu on 2019-07-08
For apt "failed to fetch"  issues, check /etc/gai.conf to see if  this line
precedence ::ffff:0:0/96  100is commented. If commented, uncomment and try again apt update command

---

