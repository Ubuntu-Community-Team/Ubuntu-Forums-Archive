---
title: "download accelerated ISO download"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by ghat on 2010-10-17
hi 


I happened to write a script, so I want to share it...if anyone is interested.... 

```

$#> cat get-ubuntu-iso 
#!/bin/bash
starttime=$(date +%s)
mirror1=http://mirror.mcs.anl.gov/pub/ubuntu-iso/CDs
mirror2=http://mirrors.kernel.org/ubuntu-releases
mirror3=http://mirror.pnl.gov/releases
mirror4=http://mirrors.easynews.com/linux/ubuntu-releases

isolocation=$1
isofile=$(basename $isolocation)
targetmd5sum=$(wget -q -O - http://us.releases.ubuntu.com/10.10/MD5SUMS | grep $isofile| awk '{print $1}')
fileprefix=.tmp-$$

( /usr/bin/curl -s --range  0-199999999         -o ${fileprefix}-${isofile}-part1 ${mirror1}/${isolocation} ; md5sum ${fileprefix}-${isofile}-part1 > ${fileprefix}-${isofile}-part1.done )&
( /usr/bin/curl -s --range  200000000-399999999 -o ${fileprefix}-${isofile}-part2 ${mirror2}/${isolocation} ; md5sum ${fileprefix}-${isofile}-part2 > ${fileprefix}-${isofile}-part2.done )&
( /usr/bin/curl -s --range  400000000-599999999 -o ${fileprefix}-${isofile}-part3 ${mirror3}/${isolocation} ; md5sum ${fileprefix}-${isofile}-part3 > ${fileprefix}-${isofile}-part3.done )&
( /usr/bin/curl -s --range  600000000-          -o ${fileprefix}-${isofile}-part4 ${mirror4}/${isolocation} ; md5sum ${fileprefix}-${isofile}-part4 > ${fileprefix}-${isofile}-part4.done )&

until test -s ${fileprefix}-${isofile}-part1.done -a -s ${fileprefix}-${isofile}-part2.done -a  -s ${fileprefix}-${isofile}-part3.done -a -s ${fileprefix}-${isofile}-part4.done   ;
do 
    sleep 10
    echo " " 
    date
    ls -l ${fileprefix}-${isofile}-part* ; 
    runtime=$(expr $(date +%s) - $starttime )  
    csum=$(\ls -l ${fileprefix}-${isofile}-part? | awk 'BEGIN{s=0}{s+=$5}END{print s}' ) 
    echo Cumulative/Average download speed $(expr $(expr $csum / $runtime) / 1024) KB/s 
done 

if test -s ${fileprefix}-${isofile}-part1.done -a -s ${fileprefix}-${isofile}-part2.done -a  -s ${fileprefix}-${isofile}-part3.done -a -s ${fileprefix}-${isofile}-part4.done   ; then
    cat ${fileprefix}-${isofile}-part1 ${fileprefix}-${isofile}-part2 ${fileprefix}-${isofile}-part3 ${fileprefix}-${isofile}-part4 > $isofile ;
fi

finalmd5sum=$(md5sum $isofile| awk '{print $1}')
if  test "$targetmd5sum" = "$finalmd5sum"  ; then
   echo "Download succeeded"
   ls -l $isofile
   echo md5sum $finalmd5sum ;
   rm -f ${fileprefix}-${isofile}-part1 ${fileprefix}-${isofile}-part2 ${fileprefix}-${isofile}-part3 ${fileprefix}-${isofile}-part4 \
         ${fileprefix}-${isofile}-part1.done ${fileprefix}-${isofile}-part2.done   ${fileprefix}-${isofile}-part3.done  ${fileprefix}-${isofile}-part4.done
else 
   echo "md5 mismatch"
   echo expected $targetmd5sum
   echo found    $finalmd5sum ; 
fi

```Usage would be...
```

get-ubuntu-iso 10.10/ubuntu-10.10-desktop-amd64.iso

```

---

### Post by aNDoz on 2010-10-17
have you tested this?

---

### Post by ghat on 2010-10-17
> **aNDoz said:**
> have you tested this?
yes.. just downloaded a file... and the md5sum matched also...

---

