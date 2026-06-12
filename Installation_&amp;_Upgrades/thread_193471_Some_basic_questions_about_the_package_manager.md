---
title: "Some basic questions about the package manager"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by BaffledMollusc on 2006-06-10
I don't quite grasp how the package manager works, and would be grateful for any explanations people want to share :)

For example, I've got the 64-bit version of Dapper installed. If I go into Synaptic, are all the packages listed there 64-bit versions of the apps?

If so, how does this work? Say I download a package; is the source downloaded and compiled on my machine to make sure it compiles correctly for my architecture? Or are only the relevent binaries downloaded, meaning that every package I see in Synaptic has already been correctly compiled for my architecture?

---

### Post by aysiu on 2006-06-10
Synaptic knows which architecture you're using and will download the appropriate binary.

Likewise, when you compile from source, the compiler knows what version you're using.

---

### Post by Ubuntuud on 2006-06-10
A binary is downloaded... As far as I know, portage is the only program that will compile, others just download the binaries. 
I don't know how the 64 bit packages work though.

---

### Post by BaffledMollusc on 2006-06-10
Thanks, guys - that was helpful!

---

### Post by FredB on 2006-06-10
[QUOTE=Ubuntuud]A binary is downloaded... As far as I know, portage is the only program that will compile, others just download the binaries. 
I don't know how the 64 bit packages work though.[/QUOTE]

Erh, I have to disagree here.

From man apt-get :

> -b
--compile
--build
    Compile source packages after downloading them. Configuration Item: APT::Get::Compile.

And as Synaptic is a great UI for apt-get...

->[]

---

