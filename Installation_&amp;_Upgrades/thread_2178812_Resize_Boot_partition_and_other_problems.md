---
title: "Resize Boot partition and other problems"
date: 2013-10-05
forum: Installation &amp; Upgrades
---

### Post by Mario_J_Lima on 2013-10-05
Hi.
Apparently I need to resize my boot partition.
I have been trying to do so, searching here and there and decided to do it, but...
On one of your posts, I found something about using Gparted, so I tried it.
Here's what I got (sorry for the long paste):
It seems that I have a LOT of problems in my system, don't I?
This is what I got after doing: sudo apt-get install gparted

Can you help me? :-) Thanks, in advance

E: O dpkg foi interrompido, para corrigir o problema tem de correr manualmente 'sudo dpkg --configure -a'
mjlima@PC-MARIO:~$ sudo dpkg --configure -a
A processar 'triggers' para initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-25-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.8.0-25-generic with 1.
dpkg: erro ao processar initramfs-tools (--configure):
 subprocesso script post-installation instalado retornou erro do status de saída 1
dpkg: problemas com dependências impedem a configuração de linux-image-extra-3.8.0-31-generic:
 linux-image-extra-3.8.0-31-generic depende de linux-image-3.8.0-31-generic; no entanto:
  O pacote linux-image-3.8.0-31-generic não está instalado.


dpkg: erro ao processar linux-image-extra-3.8.0-31-generic (--configure):
 problemas com dependências - a deixar por configurar
dpkg: problemas com dependências impedem a configuração de linux-image-3.8.0-27-generic:
 linux-image-3.8.0-27-generic depende de initramfs-tools (>= 0.36ubuntu6); no entanto:
 O pacote initramfs-tools ainda não está configurado.


dpkg: erro ao processar linux-image-3.8.0-27-generic (--configure):
 problemas com dependências - a deixar por configurar
dpkg: problemas com dependências impedem a configuração de linux-image-extra-3.8.0-32-generic:
 linux-image-extra-3.8.0-32-generic depende de linux-image-3.8.0-32-generic; no entanto:
  O pacote linux-image-3.8.0-32-generic não está instalado.


dpkg: erro ao processar linux-image-extra-3.8.0-32-generic (--configure):
 problemas com dependências - a deixar por configurar
dpkg: problemas com dependências impedem a configuração de linux-image-generic:
 linux-image-generic depende de linux-image-3.8.0-32-generic; no entanto:
  O pacote linux-image-3.8.0-32-generic não está instalado.
 linux-image-generic depende de linux-image-extra-3.8.0-32-generic; no entanto:
 O pacote linux-image-extra-3.8.0-32-generic ainda não está configurado.


dpkg: erro ao processar linux-image-generic (--configure):
 problemas com dependências - a deixar por configurar
dpkg: problemas com dependências impedem a configuração de linux-image-extra-3.8.0-27-generic:
 linux-image-extra-3.8.0-27-generic depende de linux-image-3.8.0-27-generic; no entanto:
 O pacote linux-image-3.8.0-27-generic ainda não está configurado.


dpkg: erro ao processar linux-image-extra-3.8.0-27-generic (--configure):
 problemas com dependências - a deixar por configurar
dpkg: problemas com dependências impedem a configuração de linux-generic:
 linux-generic depende de linux-image-generic (= 3.8.0.32.50); no entanto:
 O pacote linux-image-generic ainda não está configurado.


dpkg: erro ao processar linux-generic (--configure):
 problemas com dependências - a deixar por configurar
dpkg: problemas com dependências impedem a configuração de linux-image-3.8.0-30-generic:
 linux-image-3.8.0-30-generic depende de initramfs-tools (>= 0.36ubuntu6); no entanto:
 O pacote initramfs-tools ainda não está configurado.


dpkg: erro ao processar linux-image-3.8.0-30-generic (--configure):
 problemas com dependências - a deixar por configurar
dpkg: problemas com dependências impedem a configuração de linux-image-3.8.0-28-generic:
 linux-image-3.8.0-28-generic depende de initramfs-tools (>= 0.36ubuntu6); no entanto:
 O pacote initramfs-tools ainda não está configurado.


dpkg: erro ao processar linux-image-3.8.0-28-generic (--configure):
 problemas com dependências - a deixar por configurar
dpkg: problemas com dependências impedem a configuração de linux-image-extra-3.8.0-30-generic:
 linux-image-extra-3.8.0-30-generic depende de linux-image-3.8.0-30-generic; no entanto:
 O pacote linux-image-3.8.0-30-generic ainda não está configurado.


dpkg: erro ao processar linux-image-extra-3.8.0-30-generic (--configure):
 problemas com dependências - a deixar por configurar
dpkg: problemas com dependências impedem a configuração de linux-image-extra-3.8.0-28-generic:
 linux-image-extra-3.8.0-28-generic depende de linux-image-3.8.0-28-generic; no entanto:
 O pacote linux-image-3.8.0-28-generic ainda não está configurado.


dpkg: erro ao processar linux-image-extra-3.8.0-28-generic (--configure):
 problemas com dependências - a deixar por configurar
Foram encontrados erros enquanto processava:
 initramfs-tools
 linux-image-extra-3.8.0-31-generic
 linux-image-3.8.0-27-generic
 linux-image-extra-3.8.0-32-generic
 linux-image-generic
 linux-image-extra-3.8.0-27-generic
 linux-generic
 linux-image-3.8.0-30-generic
 linux-image-3.8.0-28-generic
 linux-image-extra-3.8.0-30-generic
 linux-image-extra-3.8.0-28-generic

---

### Post by raja.genupula on 2013-10-05
aah!  The only thing I have understood from your question is you got no space left. remaining is in some other language. 

what ever in Ubuntu you can clear some space by using bleach bit which clear all useless cache and temp. If you launch it with root user then you can clear the packages dumps and old kernel heads which are no more needed.

sudo apt-get install bleachbit 

can install that.

---

