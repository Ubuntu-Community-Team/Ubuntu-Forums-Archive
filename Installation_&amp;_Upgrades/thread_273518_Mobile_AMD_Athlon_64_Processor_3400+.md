---
title: "Mobile AMD Athlon 64 Processor 3400+"
date: 2006-10-08
forum: Installation &amp; Upgrades
---

### Post by ewarwoowoo on 2006-10-08
Hi I own a fujitsu amilo a 1650 laptop and recently it seems to be running really slow.

I am sure my specs are wrong,They are currently displaying

Mobile amd athlon™ 64 
Processor 3400+ 
288MHz, 384 MB of RAM

Is this the right specs for my laptop or is there an issue I need to resolve as I thought there was 512 ram for a start.

Is this the best it will run? If not how do I manage its full potential and how would I go about the cheapest and most effective way of upgrading if this is necessary.

Thankyou 

Ewarwoowoov

---

### Post by dcstar on 2006-10-08
> **ewarwoowoo said:**
> Hi I own a fujitsu amilo a 1650 laptop and recently it seems to be running really slow.

I am sure my specs are wrong,They are currently displaying

Mobile amd athlon™ 64 
Processor 3400+ 
288MHz, 384 MB of RAM

Is this the right specs for my laptop or is there an issue I need to resolve as I thought there was 512 ram for a start.

Is this the best it will run? If not how do I manage its full potential and how would I go about the cheapest and most effective way of upgrading if this is necessary.

Thankyou 

Ewarwoowoov

Assuming you are using 32 bit Ubuntu, install the K7 kernel (using Synaptic). It is optimised for AMD processors.

---

### Post by John.Michael.Kane on 2006-10-08
> **ewarwoowoo said:**
> Hi I own a fujitsu amilo a 1650 laptop and recently it seems to be running really slow.

I am sure my specs are wrong,They are currently displaying

Mobile amd athlon™ 64 
Processor 3400+ 
288MHz, 384 MB of RAM

Is this the right specs for my laptop or is there an issue I need to resolve as I thought there was 512 ram for a start.

Is this the best it will run? If not how do I manage its full potential and how would I go about the cheapest and most effective way of upgrading if this is necessary.

Thankyou 

Ewarwoowoov


Most likely you have shared video which is taking some of the mem,and this would be why  you 384 not 512. also your cpu uses scaling to slow the chip down from max speed to idle speed when there's no heavy demand.

---

