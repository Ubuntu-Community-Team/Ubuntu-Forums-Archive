---
title: "Sun x4100 ubuntu version &amp; best graphics card"
date: 2011-12-17
forum: Installation &amp; Upgrades
---

### Post by petebarchetta on 2011-12-17
Hello all,

I have use of a sun X4100 M2, what's the most suitable version for it, also what graphics card can be fitted as onboard graphics chip is not the best.

Thanks

---

### Post by MAFoElffen on 2011-12-17
> **petebarchetta said:**
> Hello all,

I have use of a sun X4100 M2, what's the most suitable version for it, also what graphics card can be fitted as onboard graphics chip is not the best.

Thanks
Rack mount server, Onboard Server graphics, vga... Expansion slots= 2.0 (total) / 2.0 (free) x PCI Express x8 - Low-profile...

The two PCIEx8 slots itself would support a lot depending on how they're physically oriented. The "low profile" of that slims that down and may get you into trouble. 
Here's what I found off-hand: 
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&Description=pcie%20x8%20low%20profile&bop=And&SecondSearch=1&SrchInDesc=graphics%20OR%20video&Page=1&PageSize=20]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&Description=pcie%20x8%20low%20profile&bop=And&SecondSearch=1&SrchInDesc=graphics%20OR%20video&Page=1&PageSize=20")

I would stick with nVidia or ATI. My preference nVidia- I have both.

The second thing that may come back to bite you, is if the BIOS will support other than onboard video. Server's aren't normally geared for high-end graphics, so when I try to put "other than" in... Sometimes that is not a straight forward thing, such as Picking a Bios option.

EDIT-- Version of what? Ubuntu 64bit 11.10 is my preference. I'm running it fine with multi-procs.

---

### Post by petebarchetta on 2011-12-17
Sorry, that should have read version of ubuntu, I wanted the best version for it, as it has 64bit CPUs it makes sense, I thought the riser cards were pcix as I had an old nvidia quadro nv280 kicking around and the card wouldn't fit due to the riser having a rib I'm the connector 2/3 of the way along the large slot making me think it had a pcix riser in, any confirmation would be cool as it would be nice to get a pcie card in it if possible

Thanks

---

### Post by MAFoElffen on 2011-12-17
> **petebarchetta said:**
> Sorry, that should have read version of ubuntu, I wanted the best version for it, as it has 64bit CPUs it makes sense, I thought the riser cards were pcix as I had an old nvidia quadro nv280 kicking around and the card wouldn't fit due to the riser having a rib I'm the connector 2/3 of the way along the large slot making me think it had a pcix riser in, any confirmation would be cool as it would be nice to get a pcie card in it if possible

Thanks
Thats the spec's I read from Oracle on that. Is that nVidia card of yours PCIEx8 or PCIEx16?

---

### Post by petebarchetta on 2011-12-18
Looks like it's a 8x pcie
[http://http://www.amazon.co.uk/gp/aw/d/B0002CWPU4/ref=aw_d_detail?pd=1]("http://http://www.amazon.co.uk/gp/aw/d/B0002CWPU4/ref=aw_d_detail?pd=1")
But that shouldn't make much difference to the slot it fits in??
Hence me looking closer at the mobo and seeing the pcix in White on it making me think it's an oddball riser.

---

### Post by petebarchetta on 2011-12-18
Looking at the oracle site and the specs of the x4100  it appears it's pcix, I beleive looking at  this site
[http://http://www.ems-limited.co.uk/uploaded_images/KP%20SunFire.pdf]("http://http://www.ems-limited.co.uk/uploaded_images/KP%20SunFire.pdf") it has two speed pcix
I can see from illustration on shows the rib in the slot I'm having issues with
[http://http://docs.oracle.com/cd/E19121-01/sf.x4200m2/819-1157-23/819-1157-23.pdf]("http://http://docs.oracle.com/cd/E19121-01/sf.x4200m2/819-1157-23/819-1157-23.pdf")
Hence I think I am now needing to chase a pcix card
Can anyone confirm a working graphics card in this type of server?

---

