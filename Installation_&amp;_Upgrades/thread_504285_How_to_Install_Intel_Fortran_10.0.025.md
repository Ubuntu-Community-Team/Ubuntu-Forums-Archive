---
title: "How to Install Intel Fortran 10.0.025"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by sysboy on 2007-07-19
sudo dpkg-reconfigure dash
I choose NO

The following errors occured when installing, I do not know how to resolve that.

Any suggestion? Many thanks.



------------------------------------------------------------------------------------------
sudo ./install.sh

proceeding as a root user...

================================================== =============================
Welcome to the Intel(R) Fortran Compiler 10.0.025 for Linux* Installation

Please make your selection by entering an option from the choices below:

1. Install
2. Readme
3. Release Notes
4. Installation Guide
h. Help
x. Exit

Please type a selection: 1

================================================== =============================
Provide a Serial Number or License File

Please make your selection by entering an option from the choices below:

Please enter your serial number for this Product or select a different option.
Your Serial Number is in XXXX-XXXXXXXX format.

1. Use existing license found on the system. [Recommended]
2. Provide the absolute path for an existing license file.
Use this option if you have obtained a license file instead of a
serial number.
3. Where do I find my Serial Number?
4. Intel(R) Privacy Policy
b. Go Back.
h. Help.
x. Exit.

Please type a selection or Serial Number: 1
Installation package for IA-32.
...... Ubuntu 7.04 detected
.Checking Dependencies ...
Checking operating system requirements ........................... Ubuntu 7.04 detected
Detected operating system Ubuntu 7.04 is not supported.
Checking Kernel and glibc dependencies ...

Your platform :
architecture = i686
kernel = 2.6.20-16-generic
glibc = /lib/libc-2.5.so
operating system = Ubuntu 7.04

This product is supported for use with the following combinations :

Machine Type Kernel glibc

IA-32/Intel(R) 64 2.4.x 2.2.5
IA-32/Intel(R) 64 2.4.x 2.2.93
IA-32/Intel(R) 64 2.4.x 2.3.2
IA-32/Intel(R) 64 2.6.x 2.3.x
IA-32/Intel(R) 64 2.6.x 2.4.x
IA-32/Intel(R) 64 2.6.x 2.5.x

Would you like to perform an unsupported install of this product [yes/no] (no) ? :

---

### Post by borris.morris on 2007-07-19
Do you have the "build-essential" pacakge?

---

### Post by sysboy on 2007-07-19
> **borris.morris said:**
> Do you have the "build-essential" pacakge?

I have installed the build-essential.

---

### Post by borris.morris on 2007-07-19
well, im not seeing any errors.

---

