---
title: "Ubuntu for my HP"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by puntino on 2007-12-18
I 'm a newbie and I'd like to know which Ubuntu version is the best one for my laptop, I mean best match my hardware. 
I have got a HP6531, I have also attached  a report made with Everest.
My chipset is PM965. 

Ubuntu already comes out with SATA dirvers or I have to add them to Ubuntu? 
Thank you in advance

---

### Post by kaervos1024 on 2007-12-18
Yes, Ubuntu has built in SATA support for the majority of controllers, and your PM965/GM965 KT serial controller is amongst them.

The best way to check the compatibility of your hardware is to simply boot your machine from the Ubuntu Live CD (Desktop Edition), and see what works out of the box. This will not alter your machine, and thus is a great way to test your hardware.

Enjoy.

---

### Post by puntino on 2007-12-18
Sorry I missed the Everest report but I can't upload it...I must paste it here 
My notebook is hp paviolion **6531el**


Computer:
			Tipo computer  	PC basato su x86 ACPI (Mobile)
			Sistema operativo  	Microsoft Windows Vista Home Premium
			Service pack  	[ TRIAL VERSION ]
			Internet Explorer  	7.0.6000.16386 (IE 7.0 - Vista)
			DirectX  	DirectX 10.0
			Nome computer  	M
			Nome utente  	D
			Dominio  	[ TRIAL VERSION ]
			Data / Ora  	2007-12-14 / 12:32
 
		Scheda madre:
			Tipo processore  	Mobile DualCore Intel Core 2 Duo, 1500 MHz (9 x 167)
			Nome scheda madre  	Hewlett-Packard HP Pavilion dv6500 Notebook PC
			Chipset scheda madre  	Intel Crestline  PM965
			Memoria di sistema  	[ TRIAL VERSION ]
			Tipo BIOS  	Phoenix (10/03/07)
 
		Scheda video:
			Adattatore video  	NVIDIA GeForce 8400M GS (128 MB)
			Adattatore video  	NVIDIA GeForce 8400M GS (128 MB)
			Acceleratore 3D  	nVIDIA NB8M-GS (G86M)
			Schermo  	Monitor generico Plug and Play [NoDB]
 
		Multimedia:
			Periferica audio  	Realtek ALC268 @ Intel 82801HBM ICH8M - High Definition Audio Controller
 
		Archiviazione:
			Controller IDE  	Intel(R) 82801HEM/HBM SATA AHCI Controller
			Controller IDE  	Intel(R) ICH8M Ultra ATA Storage Controllers - 2850
			Controller IDE  	Ricoh Memory Stick Controller
			Controller IDE  	Ricoh SD/MMC Host Controller
			Controller IDE  	Ricoh xD-Picture Card Controller
			Controller di archiviazione  	Iniziatore iSCSI Microsoft
			Unità disco  	CREATIVE MuVo N200 USB Device (980 MB, USB)
			Unità disco  	WDC WD1600BEVS-60RST0 (149 GB, IDE)
			Unità ottica  	HL-DT-ST DVDRAM GSA-T20L ATA Device
			Stato dei dischi fissi SMART  	OK
 
		Partizioni:
			C: (NTFS)  	[ TRIAL VERSION ]
			D: (NTFS)  	7506 MB (2390 MB disponibili)
			Capacità  	[ TRIAL VERSION ]
 
		Periferiche di input:
			Tastiera  	Tastiera HID
			Tastiera  	Tastiera standard 101/102 tasti o Tastiera Microsoft Natural PS/2
			Mouse  	Synaptics PS/2 Port TouchPad
 
		Rete locale:
			Indirizzo IP primario  	[ TRIAL VERSION ]
			Indirizzo MAC primario  	
			Adattatore di rete  	Intel(R) PRO/Wireless 3945ABG Network Connection
			Adattatore di rete  	Realtek RTL8101 Family PCI-E Fast Ethernet NIC (NDIS 6.0)
			Modem                    	Motorola SM56 Data Fax Modem
 
		Periferiche:
			Stampante  	Invia a OneNote 2007
			Stampante  	Microsoft XPS Document Writer
			Controller FireWire  	Ricoh RL5C832 IEEE1394 Controller (PHY: Ricoh RL5C832)
			Controller USB1  	Intel 82801HBM ICH8M - USB Universal Host Controller
			Controller USB1  	Intel 82801HBM ICH8M - USB Universal Host Controller
			Controller USB1  	Intel 82801HBM ICH8M - USB Universal Host Controller
			Controller USB1  	Intel 82801HBM ICH8M - USB Universal Host Controller
			Controller USB1  	Intel 82801HBM ICH8M - USB Universal Host Controller
			Controller USB2  	Intel 82801HBM ICH8M - USB2 Enhanced Host Controller
			Controller USB2  	Intel 82801HBM ICH8M - USB2 Enhanced Host Controller
			Periferica USB  	Dispositivo di archiviazione di massa USB
			Periferica USB  	Dispositivo USB composito
			Periferica USB  	HP Webcam
			Batteria  	Batteria a metodo di controllo compatibile ACPI Microsoft
			Batteria  	Scheda AC Microsoft
 
		DMI:
			Produttore DMI del BIOS  	Hewlett-Packard
			Versione DMI del BIOS  	F.23
			Produttore DMI di sistema  	Hewlett-Packard
			Prodotto DMI di sistema  	HP Pavilion dv6500 Notebook PC
			Versione DMI di sistema  	Rev 1
			Numero di serie DMI di sistema  	[ TRIAL VERSION ]
			UUID di DMI di sistema  	[ TRIAL VERSION ]
			Produttore DMI della scheda madre  	Quanta
			Prodotto DMI della scheda madre  	30D2
			Versione DMI della scheda madre  	79.22
			Numero di serie DMI della scheda madre  	[ TRIAL VERSION ]
			Produttore DMI dello chassis  	Quanta
			Versione DMI dello chassis  	N/A
			Numero di serie DMI dello chassis  	[ TRIAL VERSION ]
			Asset DMI dello chassis  	[ TRIAL VERSION ]
			Tipo DMI dello chassis  	Notebook

---

### Post by puntino on 2007-12-18
> **kaervos1024 said:**
> Yes, Ubuntu has built in SATA support for the majority of controllers, and your PM965/GM965 KT serial controller is amongst them.

The best way to check the compatibility of your hardware is to simply boot your machine from the Ubuntu Live CD (Desktop Edition), and see what works out of the box. This will not alter your machine, and thus is a great way to test your hardware.

Enjoy.

Thank you kerveros, but which version I should try...there are  lots of versions 6.06 -7.04...

---

### Post by kaervos1024 on 2007-12-18
Ubuntu 7.10 Desktop -  i386:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

