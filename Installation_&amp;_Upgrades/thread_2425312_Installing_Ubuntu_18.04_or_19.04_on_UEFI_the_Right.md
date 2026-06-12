---
title: "Installing Ubuntu 18.04 or 19.04 on UEFI the Right Way"
date: 2019-08-23
forum: Installation &amp; Upgrades
---

### Post by rozz01 on 2019-08-23
Installing Ubuntu 18.04 or 19.04 on UEFI the Right Way


I would like to know which correct or default way to use to install Ubuntu operating system in UEFI solo mode, just it on the computer?


Computer Settings:
Motherboard: ASUS B85M-E 1150
-Processor: Intel Core I3 4170
Memory 8gb 1600mhz Ddr3 Kingston Hyperx Fury
Memory 8gb 1600mhz Ddr3 Kingston Hyperx Fury
-HD SSD 400 480GB SATA
-HD 320GB SATA
GigaByte R9 270 2GB ddr5 256bit Video Card
-Source: Cougar 1050w


I currently installed it as follows:


1 - BIOS configuration for UEFI;


2 - GPT HDs by Gparted;


3 - USB boot for Ubuntu installation;


4 - Partition settings for installation:


     * 480GB HD SSD:
        - boot / efi, size 512MB, primary type, volume start;
        - /, size 131GB, primary type, beginning of volume;
        - / home, size 349 GB, logical type, beginning of volume;


     * 320GB HD:
        - Swap, size 2GB, logical type, beginning of volume;
        - Empty, size 318GB. (create NTFS for personal files, symbolic links to documents, download, music, etc ...);


5 - installation completed.


The pc is fine but some things make me a little confused ...


1 - HD SSD is new, so the topic creation:
        - Temperature is 100 ° C / 212 ° F, but I don't think that's correct! I have a laser meter and it pointed to be 25 ° C like the others. On the manufacturer's website says that in operation should be between 0 ° C to 70 ° C [https://www.kingston.com/br/ssd/a400-solid-state-drive?partnum=SA400S37/480G](https://www.kingston.com/br/ssd/a400-solid-state-drive?partnum=SA400S37/480G).


2 - Is something missing? I don't know if it's the right way, help me because the HD SSD still has warranty!


I currently use 19.04 and I can say that I loved this version, thanks!


-------

Português/BR

Instalando o Ubuntu 18.04 ou 19.04 no UEFI da maneira certa


Gostaria de saber qual maneira correta ou padrão usar para instalar o sistema operacional Ubuntu no modo solo UEFI, apenas no computador?


Configurações do computador:
Placa-mãe: ASUS B85M-E 1150
Processador: Intel Core I3 4170
Memória 8gb 1600mhz Ddr3 Kingston Hyperx Fury
Memória 8gb 1600mhz Ddr3 Kingston Hyperx Fury
- HD SSD 400 480GB SATA
-HD 320GB SATA
Placa de vídeo GigaByte R9 270 2GB ddr5 256bit
Fonte: Cougar 1050w


Eu atualmente o instalei da seguinte maneira:


1 - configuração do BIOS para UEFI;


2 - HDs GPT da Gparted;


3 - Inicialização USB para instalação do Ubuntu;


4 - Configurações de partição para instalação:


* SSD de 480 GB HD:
- boot / efi, tamanho 512MB, tipo primário, início do volume;
- /, tamanho 131GB, tipo primário, início do volume;
- / home, tamanho 349 GB, tipo lógico, início do volume;


* 320 GB HD:
- Swap, tamanho 2GB, tipo lógico, início do volume;
- Vazio, tamanho 318GB. (crie NTFS para arquivos pessoais, links simbólicos para documentos, download, músicas, etc ...);


5 - instalação concluída.


O pc está bom, mas algumas coisas me deixam um pouco confuso ...


1 - HD SSD é novo, então a criação do tópico:
- A temperatura é de 100 ° C / 212 ° F, mas não acho que isso esteja correto! Eu tenho um medidor de laser e ele apontou para ser 25 ° C como os outros. No site do fabricante, afirma que em operação deve estar entre 0 ° C e 70 ° C [https://www.kingston.com/br/ssd/a400-solid-state-drive?partnum=SA400S37/480G](https://www.kingston.com/br/ssd/a400-solid-state-drive?partnum=SA400S37/480G).


2 - Falta alguma coisa? Não sei se é o caminho certo, ajude-me porque o HD SSD ainda tem garantia!


Atualmente uso o 19.04 e posso dizer que adorei esta versão, obrigado!

---

### Post by crip720 on 2019-08-23
/ is a bit big, around 30gb is good, but unless you need the space it is okay.  My new ssd was reading at 100 for the first month, now it has drop down to 99.  just bad sensor reading. CPU temps are usually more important to know.  With 18.04 ubuntu went with swap file instead of needing partition.  Everything works, you are happy, don't worry.  19.04 only supported for 9months and will have to upgrade, 20.04 will be supported for 5 years as is 18.04.  Having seperate /root is good when you upgrade.

---

### Post by rozz01 on 2019-08-24
ok, ty feedback!

---

### Post by TheFu on 2019-08-24
There is no single "right way" to install Linux/Ubuntu.  How I install to a desktop, is different then how I install to a laptop, is different then how I install to servers.

Portable devices like a laptop will always be LUKS encrypted. Desktops will not. Servers might be, just depends on the data.

I use LVM, always, on physical installs.  It is so very flexible and I want that flexibility.
/ will be 25G, no larger. Usually I use half that after many years.
I prefer a swap partition/LV.  4.1G in size, regardless of the RAM in the desktop.
I don't keep media in /home, so usually 25-50G is sufficient.  Since I use LVM, increasing the size of any LV is about 10 seconds of effort while the system is still running.
Other areas may or may not get any added storage. Just depends on where it is needed. With LVM, creating a fresh LV and mounting it where needed is easy - again, while the system is running.

Here's my laptop setup:
```
$ lsblk
NAME                      MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                         8:0    0 465.8G  0 disk
&#9500;&#9472;sda2                      8:2    0   732M  0 part  /boot
&#9500;&#9472;sda3                      8:3    0 464.6G  0 part
&#9474; &#9492;&#9472;sda3_crypt            253:0    0 464.6G  0 crypt
&#9474;   &#9500;&#9472;ubuntu--vg-root     253:1    0    25G  0 lvm   /
&#9474;   &#9500;&#9472;ubuntu--vg-stuff    253:4    0   100G  0 lvm   /stuff
&#9474;   &#9500;&#9472;ubuntu--vg-swap_1   253:2    0   4.1G  0 lvm   [SWAP]
&#9474;   &#9492;&#9472;ubuntu--vg-home--lv 253:3    0    75G  0 lvm   /home
&#9492;&#9472;sda1                      8:1    0   512M  0 part  /boot/efi

$ dft  # this is an alias basically df -hT
Filesystem                      Type  Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root     ext4   25G   12G   12G  50% / 
/dev/sda2                       ext2  721M  185M  500M  27% /boot 
/dev/mapper/ubuntu--vg-home--lv ext4   74G   21G   51G  29% /home 
/dev/mapper/ubuntu--vg-stuff    ext4   99G  367M   93G   1% /stuff
/dev/sda1                       vfat  511M  3.7M  508M   1% /boot/efi
```

As you can see, I didn't allocate all the available storage and certainly don't use it all.
Everything under sda3 is encrypted. It is a laptop.

Your needs and skills will dictate different answers, probably.

Whenever encryption is used, be 100% certain you have excellent backups. If anything bad happens to that drive, I expect to lose all the data and have no way to recover it using that disk.  Backups are the only recovery method.

---

