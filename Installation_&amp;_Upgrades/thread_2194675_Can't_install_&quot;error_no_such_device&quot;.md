---
title: "Can't install &quot;error: no such device:&quot;"
date: 2013-12-19
forum: Installation &amp; Upgrades
---

### Post by sashin2 on 2013-12-19
I've tried installing Ubuntu on my brand new computer. It's got two hard drives, a 1TB and a 500GB one. 
I've tried to make it so that the 1TB one is /home, and the 500GB has the / partition.
Every time I install it, it comes up with a grub rescue screen with the "Error: no such device:" message.
I've tried installing grub on sda, as well as sdb.
I've even tried using the boot repair image to no avail.

Does anyone have any idea what the problem could be? I'm happy to reinstall, but no matter how many times I've tried I seem to get the same message.

---

### Post by fantab on 2013-12-19
Post the output of the following after booting from Ubuntu DVD/USB, "Try Ubuntu without installing", Open Terminal [ctrl+alt+T]:

```
sudo parted -l
sudo fdisk -l
```

And tell us more about your computer: RAM CPU Graphics card etc...

---

### Post by sashin2 on 2013-12-20
The output of those commands are as follows:

_Output of "sudo fdisk -l"_

Disk /dev/sda: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953523055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000798ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63  1932250062   966125000   83  Linux
/dev/sda2      1932251136  1932257279        3072   83  Linux

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdc: 16.0 GB, [16008609792]("tel:16008609792") bytes
64 heads, 32 sectors/track, 15267 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          32    31266815    15633392    c  W95 FAT32 (LBA)

_Output of "sudo parted -l"_

Model: ATA WDC WD10EACS-00Z (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      32.3kB  989GB  989GB   primary  ext4
 2      989GB   989GB  3146kB  primary


Model: ATA TOSHIBA DT01ACA0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size    File system     Name  Flags
 1      1049kB  498GB  498GB   ext4                  boot
 4      498GB   500GB  1999MB  linux-swap(v1)


Model: SanDisk Cruzer Blade (scsi)
Disk /dev/sdc: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  16.0GB  16.0GB  primary  fat32        boot, lba

---

### Post by sashin2 on 2013-12-20
The specs are as follows:


[LIST]
[*][IMG]http://ubuntuforums.org/image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQH/2wBDAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQH/wAARCAAoACgDASIAAhEBAxEB/8QAHAAAAQQDAQAAAAAAAAAAAAAAAAUGCAoBAwkH/8QALBAAAAYCAQMEAQQDAQAAAAAAAQIDBAUGBxEhAAhBCRMxURQSYXGRFSKBQv/EABoBAAIDAQEAAAAAAAAAAAAAAAADAgQFBgH/xAAmEQACAgAGAgICAwAAAAAAAAABAgMRAAQFEiExQVETIiNxMoGx/9oADAMBAAIRAxEAPwC/oGw/9AHxxr43vwOtfY/GudhrXQPGufjQbANgGwH99D9/G frjrll3sepjE9pOXqLgZpi17Yr1kiAGbrdrudhTx/igpvy3LP/ABalqPEzrySmE1W5Pcjo6MECqO2DY7xNw7QIMVp3ud7uMptXjidytGY1qySiCMvFYAqTRiaObuwWFFtNZNyES22QBWTbuzquqbXK3NptGj58yIigxcuUNWDR83NFFO3xwQTrvikle/kXdtJRIhI/8rUb1QFhVjvEDIoJHJI4IA6v2TQ8 8d2H1prcZLxNfkrBDx87Pmclgod5JNG0pMGZoGcuyxrBVcrp6LZAhl1vx0lfbTKJz6Dpf38j rwIDwbgQAPHjXz/wB1z4rWK40oku7j0rkvHoyVllmjtHKL23WWRyWKUdJgk3vsFlW4yStyYKQjn3nsCspMnq1mZpyKEC/gZ GVjTSDxF6g2S8Jma1nOAvs/wCNGhiM2uU6jFpJZdrrFIfbSXt9KRTat8gMUkSpmVl6smhbUyAf8 Is7ki0y7fLokmwHKyGdwPtE0YiduaBhO90ejamMushNBA7EovgkskEUAau7Hjvqu  u7qrPdDnjnet DD58fevje AH zryrEuccSZ3rSdtxFfqzfIMxipu1YKSRcPYl2IAY8bPxJzJysBLI70vFzbJhINx4VbkAQ6OsVkZGZHVkdTTK6lWUjsFWAII9EYYCDyDY9jEJfUS7Jax3VUN2vKxhph0wjzkcKu5uwpmpzaKbSD9C7UivQTZc83dY4x1WbeEVcRrSbaPVmij1oob8g1Z4Ml507IZ1DFWb2aN1xnbBaDj69XCKetGFkj4x2uStBcIZCYa2Gn2NoCqoRJJOQi3z1i7XaLFURdP4JveQANhoR19AAh5EQ38ed644 vnQQ77huzbFGeIGyxkvWIhRpbF3Erfq0mxjmMflp8yjgTgYq4zRGZ5li1QetkSjJwrppIps3swiVUQlHZj6umatLkPwyIMzknYNJl2NFGsVLA3cUooE19XoBxYVkW8YbkHaw8jyL6Psf5Zrziq26zrOXSfV9sxnsvNyT12hGRaAN0AeSa6jxwlGxjQhGzNExzGUBBqkmkmmQBEAKTYbsn5qp2HaZLGscoM5evbQTO0jHRhj628M7QM3itkKdxLT8imB2J49JAp26rgyZETLoAZZv9x3p8dwvahNyMljGHtuTqDWYtKz2GpQUwoxyZgRCaWUNAQ9UyJOOGkZleFUYHcMztGqi8rHqQ817CLZkk3M8m/wCn36S96nLnCZf7p6 eHs9dNCzNdxVJozjWFxhD2SLsB4 erdrYOnERd8uxwowslKyMigqygH7lJmVNorGrRrvrptX0iPKx5qOQyCqTJpSTtKtfSTsxRrYLtRU87WcbQ6BG5aiCDYtjyAPY55Ndc8fvp3 jL27ZLeZ1sndNmGZuNWslgpskyq2N4toolWSVl2jXFEVL/LNFV4tSxnaTLFzG0xyVKXgRZLPZEBXURWVOrIdJodbx/Elia5HtmgrAyUl5EG7VOUsckyjI ICcsDxuggaWnHTGNZpvJNyU7px7CfuHH9IAB1wmezc2oZl8zOV3sFRVRVVI40FRxoKsKi8CyWPJYliSbKKEUKL48 Se7P8AfP7w8S/XI788 RH9g PsPI7186z5DWx4 f8An98 d6Dj76OjqriWEGxVmvW2JdwdnhIyfh3pkDO4uXZt37FwZqum7bHVbuE1EjnbuEk3CIiH6klUyqJiUxQHpcKAF0ABoCkApQDgCgUADWtf6gAa1vgPn Do6MGM8CHICGh/fjkOAEA1/X8fY9HR0dGDH//Z[/IMG]**Processor**
AMD A4-5300 Dual Core APU 3.4GHz, 4MB Cache

[*][IMG]http://ubuntuforums.org/image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQH/2wBDAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQH/wAARCAAoACgDASIAAhEBAxEB/8QAGQABAQEBAQEAAAAAAAAAAAAAAAkKAQsE/8QALxAAAAYBAwMCBAcBAQAAAAAAAQIDBAUGEQcIIQAxQQlREhRhkQoTFiJCcYEVMv/EABgBAAMBAQAAAAAAAAAAAAAAAAAEBQcG/8QAIREAAgMAAwEBAAMBAAAAAAAAAgMBBAUGERIAEwcUIiH/2gAMAwEAAhEDEQA/AN gZD QB24x2znwOMe49sc5DGOu4Hj9wcY5xx/5H64HjnkPPtx186rpBumoqsYqaSZDHVUN8IEIQn7jmOJjABCFLyYTYAociOAz1OrcR6rWx7bkdWJs2s8LcbmRRZshQ9Ljp32xqv2wAKsW7Vg3CkDCPkhUT ZbWCcilm5FCHVSAFEwOtYuVKsDNmylPsvC4YwRJh ZLwoJn0w5GJKAXBHMRMxE/LWLlWpAlasJRBl4XDTESafUl4UEz6ayYiZgFwRz1PUT19R3nA8iHnsbj9ucCOR/vGR/3t0zyPI9h8G44DnHj3/3z4yA7kPxHt3cSk/U9CdPK7pSDRouEfadT3Ks/YHzlZv8TBeNiEG5K8wT/OOBHBH7eyt1RSUTZuDkMDoJO0H8Qnr5pFqxBak6sao3C8mLZYwlthH8 7/SMhD/ADhRnoWFrEauWlMyysUK5GiSUAaRij/KS0AuzcNBTfTG7DvMMqZGlbRBr/RkrCqyEyyAeaalol3XNrRP6lWmutzliQ1YfYlSGTj1nTEMq5OhZTEgTGEC6jPxk/DjTUtmq41teO2mg66TYsZivLnStR jBzxznGfBh8 PfHbOeAH7up3bGvUg0E3r0Gmz9Wn2tfu9xjJSYZ6ezAS7CTfRETKyMcE1XFLDDV9WwRkg0jxmkyNWwycYyVOjMMWbpi9AjqhQv09SuNqhYXaQUyMkuZ9LYPUGh6ygW17Kinw s8FvQyCW1YGJRD9G9U0kRZovXZTJEBEE/wClNCfLEPWXTEWFF/h1dwrek4IGrAxIYhZ60OjPqJTN4vMypP6m2Xaou jpWJfUm1s46l0qJknsXX4isWjT LfRMzPyKtglE2DxRWPsi74i7KSayByOHMDHZC9Y7zqhXzxsEfTCUnDlOqhXrLQ4hzItHhUjmOsms6h0TKNy/EiqZyV ogCIEUVRdFVbLHS9am9UKoam1Cfod8gY zVG0xq8TPQMoiVdjIsV8fEmqTAGIdNQpFmrhAybho5TRdNFUXCSShM324v0z9U9uOrxrNsR221DUCp2Vi3Y0SCsz6Ctlb0atC8bFspWbkIbVayJKRJFpeNNcGtorrieIu7kJWNmqucyUau/yrkdPlnCn39/ieazm9bUtiVzjelfcOjWvXHkP93L2Zq3rFLIqLiuDcz tdWlYy2ouv05k5xYx9biW83azpvb/Htu773Mx6n7O7mW7Rs8aGA82pcGZW81kHik6a6gIn1jpxD2ljWpexDdZqyvpZYtYp1fQLSjVCZXh4ay6q1CwuEyGaM1pOSYmdxSCzB81NENTPYx40ML52QjoycS0 TM86q7tS2UaEwt9lKPsY2u2/fdrE0kJGvWbWrWNedgtr9WQMcirGYalklo bXdRb5Eix0H0jHOPibK/wDNRlBcpukdGO030XZ39Yw tXqF6uq7nrtHR800gdFXbckhoHQm1iaO2r2Pia1KtEotRJim XLFM4GArMFGqkbrs4742rRRG69D03oeltajKZpvT65RalDNyNouuVOGjoGGYoplApSNo6MbNmpBNjJ1PygUUN8R1DmMcwjNXwXnPNoQ/wDkTk7s3LMO38N4kTcmi3pxsWGlpJsHoaIzXYNW1Ws2nZzyR/YCignSpXT0lcluNsOfYVj0XOA6qSrVbm8msKkdqa/9rOJVYxwG0GBRv6NOJAUakT2UR92Y ltqbp7qxS9z27fXdTUrWWlRajKlacaZQUbRNE9Om7iFkIIGbWKjmjNxbHUfGysg1bSMk1YCUXALHTdKlBUzq24547Bz2455D7eR4yP 9OtawOPYvF85OTgZtXLzkRH51qqhBfqIAfZdxMkciADJTPfkYj/kRER0FGjWzgaFZc rDztWnOYyzZt2mQAstW7Ng2Ps2GQsINrmGZQMD31ERHC 3I588 RH6B29w8jnHfHfIYyPHf8Az78 c4Dj36dOrPzf3M8D3 /0zkBxjP8ALAc556Z589hwPP078Z4znI5DnPnp06Pj5wIcgIYH68chwAgGPt/XuPTp06Pj7//Z[/IMG]**RAM / Memory**
Latest 8GB (2 x 4GB) DDR III 1333 MHz Premium System Memory

[*][IMG]http://ubuntuforums.org/image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQH/2wBDAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQH/wAARCAAoACgDASIAAhEBAxEB/8QAGQABAAMBAQAAAAAAAAAAAAAAAAgJCgEH/8QALhAAAQMEAQMCBAcBAQAAAAAABAMFBgECBxEhAAhBCTETFFFhChIVIkKBkXEy/8QAGgEAAgMBAQAAAAAAAAAAAAAAAAYCAwUBBP/EACQRAAMAAgEEAgIDAAAAAAAAAAECAwQREgAFBhMUISIyMYHx/9oADAMBAAIRAxEAPwDfpTdP5Up7ca9t78V1r619tc7prXXdV4/dTjXOuP8AzX76rxzzTz9OOq vUw71hew7tYmOcUQAXWSj/GZog1n0JWEWkBDW6FgGOILdYu7FMohASFHWrYMuSiORbcnZcpVO27Ohiz8QnnEmCMEpy09sQMtlJrc2tEDhXb48ykQso8xdkZEGN3asjLSBzcJc4FtZYjWRFxTW1ZRNiqkUcvdfZDk5LCcbWKaLCUzQgHWzpTsBQQWJAA2P6kFJDN9KFRnLNsLxUEsd6I2ADofs2iFDH662ac6rzWnn2u4/bvVa7r/3W6/37dN815r7V8XccU514 v9 fGOVq/EKd0wbK9juGFGx3sYnw1nbspu LsgxeOSp4Z7RXCQQx2hKTyvIcfS0AVZBpaxXgs1I8olZ6cLWxub1RjJbZh9cXIrGlj1yw7HMPSFhmwNCF3qaoyJsAZXSv6woRGHX803ZHMKSAIt4tSW rReDbaSsRV3ssTRTU6ToENwWwoE M1ZJkkFS3tWNHRnmCro7JyKOjK6rtS1C2DcGCVEnVmW5m3o2pUMhqAUDrzQkE606fZLAdaZOeOd634ur58fXXtvfFK/66g12Cd25fd1ht2lsmaGiOZGhE0c4JkSMs1CEwG13QbmmQthQI5rk7FpgOkff2slC8hwK2TYckmtdahW2x0KwZQw/g/51b1Bv1Jcy9v0hmTzhLIVYY/TWLRKOUhkdnQEoLjP6zOnarjJHMkuMsr8W3lt7DH46Gkci3/EREfnMFUwNI9S6mZ/1DIb2 ZJdYFivECRUEq5kWHOE7x0MeyDpCY4GUc6XCEOLHW5J1icijkbTGOt KccJI20OOomHpEkJXtdzPpa96uRsiSbJEQmmK3wgq5BEMZ0lr FI3ZoYpjI5M2hJEFQRJmjZsrEexG6YfLEEjE2ttqSZdqSn5 vG5x6fXqtZgjsdxxlNvw08wgshE5wrZNxaUiarW32BM6HwiBTry77rKuABhjUCSqG0ONKNVRj0aqUWaXzZjKtLG7rDNyfYk3mqZU8X8UilxOdfVROAFFm ySAHPPajRxWm4WeTZFxVYNXGWjK2QraVkDCJU7VVOmpIAs 3I0ozywHC VYDBLsWSeG5Zb5tJZPedXJ8zhGRaIy1vcWRZ4cAXeeLNLfDbnY qQzC2WSMwe8lYmqobmWYAk1G2twGXpSXtnxExyc/wDUJs5QV/EdLEGdc1IGw/IZmJYy4KfCZ1W9F5EHzawRFwUsuTJsqWY9EKXNwC74LZpmz0 e /O8GpApi0YOXZ0XhvfbEV587koHOTUMtVuVeELoPVI2jc4LWHA/spRMsccy2y0wIRfqPkn9Gvu/eosuxtYeIGRxq NTkM7j5Oe0aoN7SSiak1/LBQEZRS5UkNtKKKWMUqc6Nre9kpVdRaK9YmVg9y887S696l3nw3KplIipgWjXNjKDe42TOjymZZXs9TY/qUTCXBVjSfoYPG/Im8R7zDuU 2 P Szx8e8vgd8xvldrsMmZiRXEIxXFMYcXm6P90VKcnJp7Pf8Asz7pwsK5yx7E38JlQau5CWxuBPy4tRGi9imE4jj69wYv4KI 3i8nL0TzRBlbSKoLDAvcTUoWoOKgOU6hXgr0De7rDvcFjPNbXKsWpqY0yNGpxG296yHIpAEzLtEio7krXjXY8tIdr/lSXNIdG48C75g9dWiqVb77KumzDxMjt0VxxmtlqNMr0xnDrsKGBP5A8n3TQ0F5lf1 gtNFbn2NfExy7MfUtLMEXkAo2VJ lIH5M51osxO97FrfpzXfnnzWv2p7fWnmu9e u aa3Xj3/r/efO9U4 vTp1r9ePrm K / /be6V1rf8tU53z03z59q6rz9vfjfG97runO/PTp0dHTitOaVpqv345pxStKa/z/AJ9a9OnTo6Ov/9k=[/IMG]**Motherboard**
Premium Asus FM2 Chipset Mainboard with Integrated Audio and Lan

[*][IMG]http://ubuntuforums.org/image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQH/2wBDAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQH/wAARCAAoACgDASIAAhEBAxEB/8QAHQAAAgIBBQAAAAAAAAAAAAAAAAoHCAkBBAUGC//EAC0QAAEEAQMCBAUFAQAAAAAAAAQBAgMFBgcIEQAhCRMxQRIUFSJRChdhcZGB/8QAGQEAAwEBAQAAAAAAAAAAAAAAAAECAwQF/8QAJhEBAAIBBAEEAQUAAAAAAAAAAQIRIQADEjFRBCIjQRRxkbHB8P/aAAwDAQACEQMRAD8AfnJsgQBpjDjBwQx43SzlFyxjCwxMRVfLLPO6OKKNid3Pe9rE5Tleqs5bvy2W4IZLXZZun0Ip7EaRYJwJNS8VJNglaqsdHKIDZlTska5FRzXRI5qoqKicKnSpXipZTk2V I4fpXqvuEz39qTwJBcS0CIujsSx4ywNsRJJ4UbSpUpl1SVXVmOH19ecacQllLYeXGiusYi55otpmkwOIiVtCJi2npJ9TUWcNpS4vjUl04axHGsx5Wm3OKZKPKpAsqtJYWGj/glSSM9kyfD1XxhG5LJBooAa85XsTiA1SmnTV/X 78aZOwjextI1JtoaDA9xekmU3ZVhVVQNTU5pUT2FjY3SxsrQqwRSWz2c5D5o2rGAwn5eRVjJ8l6Oa20DXo7lyO7d0XsvZUROfRV44X/O6f0klr3onpWAPBMLV0xORU8UJ4OW0FWPQ3wdgE1r4LGK2oAKIoSzjmicWwoEWtSGZ3A8LY0je zXhO MJrjlmdai6Oa6kF6yaMaWS1eK43rRVCDlZbXmvRhCgZKdDGkWo0oIEiDk2lbNDaDQgOmMS9PNie4IslIEnjHk9XV0uP3/AI8amSQjykkRaz5q/wCzTavft35459nL7 3549OeeyL/AKddWxLM8XzmiCyXErytyCjsW/GNY1pMZEDnIvD4JVaqOgLhevlziEtiJHmR8MsTJGuah1Ome4GPuHpMj iY0u/ oY8PtdwWg4 4/TmpR q2ijobYtQo3RGW2OhvcQ5XEDtQhslfKqvaRy75OKZ9i1ria4Hy1gdCNbNy2s1wCdgeuJ j9NX4dhWAZNbFyQiYo6wwPCEp6KG5rTarIvpWRMraX6DOVEM1ZrMKSayNhMSSOH0sL2krckprKhuQxz6q4BKrbAAmNsw5QZkT4Z4ZonorHxyMeqKipx6KnZeOkS98GwS08PTUzXLWPC9Wq3SvRuXN6WzyWsyCF09Rf4PqRMRXDB00TiQIByocgjdV2SNOGe0iWxtPjUy8YR1E4ylTGiVhb0CmW/o7r702cYRWd8DKHf11WbwGt/qntZyfc/hUGH5Zq 25FnbUT5bnGDGPpqSzHr62aBCC7hZzKM8XzZvnLGEcQVLCcZg8lYC16lsnvRE3bJst0codKdHh11Hmx6F7DJaQymjS5uiHzus8kyjJSpoA/NNOHIeZ9NgsZRVRgwVesEMLG4gqndlqFuIOA042maKaq7p7tixV9dI6rfh2iNFyrIIeBJQwagtgfCSRc0c5csDFaBfzP4VuYHb9 n63Z7l6ety/ftuJfg2LXrZIjtuekohtHXB0krWSQxXN8Mcp1yW1WKsENsTYwifc5rkX4Y2b7c4bBibv7vEJSgRISlgffylGMTtDm9SBUdedM9R6pjxh PtWy RmLgOXBGTJowkIGQzeuX2YeJNfX2 7SDR3BtSsbBbqLn1fiuW6VadVVpm2O/THTxyW7swzNwclcJfA1qTyhzoHiR9fM1nmssBWqLIdMVbLvDQ2ebC6KGs266R47itugbwzMwmFYdl9iyeV85bSr0zzrF0RREkk0sPzHlKrkRG/a1UOlOfNJcIxaLLXIF5ON LovDR1rfZ9O7MOBu7ki1MRAumg4uLF7e3V/G/juvPv391X E9PynuvPHrxTfeNsY0D304VS6fa 47LkeLUuTUuT/ToSZBorIqhL frA7RjPsPAHORhjBCo5RvmYopXRPdG3g6Oo106k7RDbLoZtzxsHFtHNNsWwiprx4xom1FWLAS ONiNb8ZTY/NVeO6ta9rfX7Op54Tn39Oy nHHHr27dvde3H/ODo6NGteyp3RU4X e3dOyKicf5/X5Xo6Ojo0a/9k=[/IMG]**Hard Drive**
500GB SATA Hard Disk Drive

[*][IMG]http://www.jw.com.au/images/cache/40x40xf7986071c70623b7c21b3bf271070b2d.png.pagespeed.ic.TqTJJZV7Z6.jpg[/IMG]**Graphics Card**
Integrated 2D/3D Intel Graphic Accelerator

[*][IMG]http://ubuntuforums.org/image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQH/2wBDAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQH/wAARCAAoACgDASIAAhEBAxEB/8QAHAABAAICAwEAAAAAAAAAAAAAAAkKAQsDBQcG/8QAMRAAAAUDAwMCBQIHAAAAAAAAAQIDBAUGBxEACCExQVEJEhMUYXGBFZEKFiIjQlKh/8QAGAEAAwEBAAAAAAAAAAAAAAAAAAIGAwX/xAAmEQACAgEDBAICAwAAAAAAAAABAgMEEQASIQUTMVEiQQZhFBUj/9oADAMBAAIRAxEAPwC/ai5QWFUqLhFUyCnwlyJKEUMgrjIpqlKYRTPgQMJDe0wAID7cCGucB6B7g6fgMAIecZ78gH18agT3fJ3Q9N2p6V3A2MUUqKlLsSkpbW8kXVAvXtFQK8y /WaIrQsS2fjJmqWIepu4tnJGUXj0qddVMSSaPTrxqsd8ZtT9bpa4 /ie2R3yt1TdEvalGkErO1bTtXsZVSSkpG3sI9koGeh0yqqqSc3VjSpJFoyZLhMUcxftYCposxICQqRXNGZgS67CGC4JXJyAQVXO9lweXC7FOVLBgRpXlhWRYhIDIylwu1sqAdv jANGjMeVjaTuMmHC7SCbEHOB5EO/Q3H9OcCOR  Mj emmeR5HoPY3HAc47efz37dRKzMXBRzqXmpJhDxTBEXD6SlXraPYMkADAqu3rpRJugiUcFMoqoUhchzzqIrdP66np47Vpt5R87dc1z65ZZB/TNoGP8AOyUOAouFSLzdRMlS04xbf2PaqDWSkJBIVW2I5QrlH3uSAcEjPr79ePOlkljiAMjqmeBuOCT6A8k/oZ4yfAOpjAHwIDjPYR6jxjz4zngB/dqCv09PXKslvku3UFm5Skz2fqh5JP0LVEl548syr1vGlOqvGlk14mGbJVKux FKxsa3TV/UWyjpo3Ez9idJw0KwYZByMkeCOR jg6I5YpgTFLHIFIVijq21iAdrbSdrYIJU4IByRqTTebY5HcftfvZZf5qSYvq6t/UUbCv4VykzlmdQJsFnMGtHuV0l2yS4SSLdM3zKC7ZRFVVFwko3VUDWs4tztmY2oql9em2dfz9r742XvvEzatOv5ZZSrKTdwEo3nIeagVFoNnHPUWbsqJJdtMyzBB2ujKslAbpty/G2sokKcAA3bPtABwIZyGch5AcccYHjrgIKd5vo22m3AXVLVdNPwtrGXeqqTWu25hYIJc6rl7FuHy75kwcy7eObrz8izUBZ2LMyTWXlDvXTZ83U C3m/wAkqdbsQ0ZuhXWqW6fUqNiWIlRBeorYjS/Rshgd0c1N52iIKNHbjrS7wiOrdOj/AFrLfg6lE7RWun24IpoGMdmtaMXcpz15l cDLZiijldMsasthV ZTFLjcXuG3/7ragZ1dVNZ3k3AR9CyLdao2jB/UTq2kawPJLsUZ19S9Mtm1BQKaoukoQrJxHNGLlRBcVFpVSQdvD 37d/RN3u7xJ Kq53bx3RdMP0ljLVVW7FGlYhRi/OZcAM2OmX5srUFDEaN4hlMpokIgmQCkRTST2MltbRW8tXb DtxRNF0nTdKQkc0YJwdP0tTdOQzlRq3SQVeKwNPRcXBIuHh0AXcA0jm6HxjZTRTIUhS lFSTIAFImUpSlApSlACgUAAAApQDAAGAAMBgOMj213DDIxVu7jCgMVXDMfsg5OAfXke MaiaX41FE8Ni5cvWp4HttGn8maOJYrZibsyFZDNK0Pb2iZZou4WkdowZGGq5uyX Ha2 7bZOna8uZW1RXHuHTslCVBBngHLuloyl5yEcIOmbqLlEFTTS50lm6RRWaDBkUTKQAbE9hB01Y0xjGMBkeQ/2wIY65x/0Q476acV4gANpJ9szFj ySck8eT9capIYoq69uvDFXjzntwosSZOCWIQLudiMs7lnY/JmLc6F8cjnvz3EfoHTyHcc464DzjqPGc9 nAh3yP1wHGmmttPrHQBwA/bPbGcgOBDP WA579ONZzz36Dgefp14zxnORyHOe mmjRpwIcgIYH68chwAgGP2 3kdNNNGjX/2Q==[/IMG]**Sound Card**
Integrated High Definition Audio Chipset

[*][IMG]http://ubuntuforums.org/image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQH/2wBDAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQH/wAARCAAoACgDASIAAhEBAxEB/8QAHQAAAgICAwEAAAAAAAAAAAAAAAgGCQcKAQIEBf/EAC8QAAAGAQIFAgQHAQAAAAAAAAECAwQFBhEHIQAIEjFBE1EJFBUiFiNhYnGBkUL/xAAZAQADAQEBAAAAAAAAAAAAAAAAAgMFBgH/xAAmEQABAwQBAwQDAAAAAAAAAAABAhESAAMEITEFQVEGInGBE5Gx/9oADAMBAAIRAxEAPwDf0DIf9AHbbHbOfA4x7j2xvkMY46GOJS9Q4 3HcekMY75EcZ874/nG3CY2jVfU6Rst1gaw6ZRjaszryHTVZsUXD85GyDdQp3J5FKTRBRf1jYOg1RKQOjAFMICOBJmX1Kn0Vizc1JnSXRamatpSblGy7h6uuKayKMFIFatXqrZL1BAkczKiYwgVoqsYwF4umwSAVrSl207nt8efrvUfy Ek7bx4f 1Z 2kWT0yxGjtu5MgcCLg3XTWFA4lyCawJqGMmYxRA5SnABEv3AAl492dx3HsPg22wb48e/wDfnxXdpRD2msT55RlIPGTZMnoOxCLXax8kdNwYSi B4zi0hbCiomToEHq6axlFWTxEREij0V6ytZhEElCi3kEylMq2MIqFOU3SALtVTAT125h6Q68AdMw9KxSj9xkXbgdKmCHccB 31r906FSHDHwfgb N1Kd9t84z4MPnx747ZzsA/wCnAA5DIB37gId84HzsPcMZxjfH6HE6el vOnLeJnZPUyqxxSysg2TJc45qUSfiBsxTIVtLlSTD8 cjWyCTYgCBTvo8oNjLFVatCKVSc23xRNNuWzVKlaH1vQjVLXzXe VVK8RNc02hmAwkbUzyM1Dspm52RuhYrRDsX8nXpaOQ/D1Ctr5w5bAzasTu1UUD3t9IGDBsdtgz 4Bz/YgGMbe3fHFN3ND8P2wvea1/zfaMs2tvktSdBE VvVzRWysoJaiztAG/ONQ/rCYyirQzJOQfv5eJsbdooLhRJ hIxarNwm6MrVCpKSlSogkCSnISHDk77DgafXZzUlpIBUkOQCY8OewDAs55LHyxqqHUj4k3PTc3KjBGV5cOT5g4dfI/QFnLrVTVRVdZb5EIxtOWSOmbzUpdN0AN3qVm5D1GSLk5AdSbMhBcnV1W4T7yfqOtt45ztfLzY6VdglmE3Y Yid0JnqtLV2RMk7a1ujwMXqTV7hVJRqZxFPmDrlE0ILZYB08izumpHajpB/8AVD4YUhqDOWjT1DUu8aH/AE KQcxdGbRtalqLFNJw7lFb6aWtrUxWWjUipnSYPPlVknA9QyjlWcRlY2JkGjPwkdEq60YV3VbVe2cyR40yKAUijU0sa2BRACEFCVm4mRsi8aCqSZE3RHNhqZ1BEx1XRFBBQeiy8H07j4 NdtdVys67eCVZGOjHOJcxU 0qgq6m9YvEuUpKVMOXWfYMrAu9XyU9QGZYx lX8Yg4BZWfj9RAVu3cVaXbu4jo0m5dtqBXsoCN1sJaD6qQGtOk1I1PrkmlKQ1yhW83GvU0lW5l2DxRQ8e4WaLlI4brOWXoLmTVIAiZUTED0zJhwcY2pmntvYsKjBVqnw kVIqxK4xj4xKW6JtKuVoEUY6vNoKnqJV5lGEYIfIpNnk5LIpIqGMswMvkROOaXGaoShJUJEFUHMZEAAqi0iAAS5AA1WyHYSaTB2BAdtsCSQH4BJLd6aovtuOfO/kR/QO3uHkc47458hjI7d/6/wB385wG3vwcHC17UFtWm9Kuztg tMAzmV4wFCtSuxWFAxFOk4pukE1SN3yRDh6qSDxNdFFQx1UiFUMYwyeNiIyHbJsYpgyjWSJAKi1YNUWbZIpQAAKVBsmmQhQD9uPI5yPBwcFFfS2ENwEMD u24bAIBj/P49x4ODg4KK//2Q==[/IMG]**Optical Drive**
Dual Layer DVD Rewriter - Supports Dual Layer (8.5GB) - Bundled With Nero Essential Burning Software

[*][IMG]http://ubuntuforums.org/image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQH/2wBDAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQEBAQH/wAARCAAoACgDASIAAhEBAxEB/8QAGgAAAgMBAQAAAAAAAAAAAAAAAAkHCgsCCP/EAC8QAAEEAgEEAQMDAgcAAAAAAAIBAwQFBgcRAAgSIRMJFDEVIkEWGAojM1FhgZH/xAAXAQEBAQEAAAAAAAAAAAAAAAAFBgIE/8QALxEBAAECBAQCCQUAAAAAAAAAAQIDEQASITEEEyJBBWEjMjNRcXKRobJCc4HB8P/aAAwDAQACEQMRAD8Avm5pmWN67xLJM6zK3jUOJ4jSWWR5JdTPNIlTS1ER2bYz5CNgbnxRorLjxo2BGqCqCBKqJ1VY70f8RzGBbXCOyjCXJTyjLgruPZFd8TAmY/CE3D8KV1xyR8ZF8keZlBx0X9hO0Bt jsIfUBRP7H 7NPFEL 33aip698piNpzwvvj8p Pfv16ROsySJFcJwT58VQUJCX8jwil f vSf78fz76W8M4WjX5k6oyacwI/pTKPUd9Xba25gzj Jq0ZRhTcuaKrYv2NFLlr9u5i4H9Ljub3fs O3nefbAyTO8zv9c2Mq7s8hyYIrCOJuzIYRvN/cg9AhlDrmxjwIMGtFlyLBGtb 2BG G1Qd47Vj3VsIQMnYjsuEYS5lhU5LWTmPmQGSjRa2q  iOPBw4DBQ4wA0hfLIc8UJUMfRQrcdyCgSkyPHbfJa9dLZc6VfUz0iuA/G3/buNSDA7ipZefF58SgK8sn4n/MhaBPIicM5qzVUC/ffh6/2TGkHIZRwLKXEu2m1dNHXXJDdra3NdF8yTzE44sKLQkDYiK KtcilKSSpQQLAxEASwaW228sEFWoSjlqT1svU7qX7 Rhk3b7siXtvVWN57NhBXyrgrhh6KKukglT3djSq8ouNtG2cn9P 5cZJsVZJ8m/aCi9HUYdjXC9s2v/ABQvH7jL0RHEaFzxHNchFEMGUFoTEUQFERERUFQOR9qdSVQCcwLBOQHuMzY/jFRBWEVvdjHffY3x136MrI7Ku6pkUUid0JtBpOPwvniVonjxzx7Xj/hPXC8cdZrSY  yH kqEqCip754VFH0vPHPHr11pj940Fyy7Ue4muabN1ybpvYMUGGwVw3SexqxBBEBRSMjUkQRFF5XjxRVVE6z/wCw1y2024nxLy2nC/tHj0qoq8qiev5/j/z8N DepX c7a rH6/fbtgXxX2lPyin1T/Ww0z6MJuPt2tSzZy6memis/ZgzWJNk2ESQ7vSSgPyo1VaUsiaww66y6kYLOIbntG5LJEpJ7k1zP3BJ3LkMTJ 6fW2fVGPLAOx11hOE7Pp8hgONMyWZvz5bb71uYj8Rya5DcZccxicgMNOsEC/dA43U4zHdGytIZPqWpwjZGea3rbbGtp1uWuYFlVhh1pa0AbXxqWbBWMAH0 ZuJJmOV7sqDYx40l1HygSg82XIgzvdyzMy2BncHcu4b/YdxCKjqLc7cseRqllTaRlf1iypf0 ReKtVi1cEdoYVLEjeQi1BEgR8Wc0IvVzVkEYFOGeOZTWosjJDLmvMzJLKZbSucNOnKRNJUIlOBVkVahCc4tSFPLQE9JVGZPllnlxqTvaDjTI7DjRzta1o55Evyf1S4ikRGSoWZX/AO4iNVIlVeVUjVVVVVV5Xno6i36TciRL nb2pSpT7kiVK1ZTyZL8hwnX5Eh96S688866RuOOuOEZuOuETjjikZkRkpKdRdT2lT55fk4qIepT/bp/gYYc6y1IbJl0BdacAgcBwPkbcA/RAYGniYKiqhCqKhc 048kVK3e39JvE9qtXexO3huuwnYkhZU6xwx4wiYZlUpwDN1a9UZL mriSakXm3zTyHi/zmIZmcoTo61Sr1eHkTpSRuXHWKXNE2T 9cYq0adaOWpEkdnueY4pAd/Xb5t/Wu19cYvlmvcxpL Lj2zQlVVhRWASWZc7MMXlfEwseO4zLZkJ5PQHY5ujKjL8zRuBwvUUa1 n13nbdtxXB 2zb1y1ZJCbhzTwy4ra9xBbVzzWdaxoUVG0F3yUlc4VPaJx0dHVBU4yrCkSCGZhGV0d010zGB6XC051JkmdoKRsm0ctr9L72/xxpV/Tm1pmWneyft31nsOjk43meG69q6fIKSWTZSK2wYceVyOZME40SiJD7A1TlVRF/KodHR1OSbyV3l1Pxlq/dw6BEIl7EYhfexEx/9k=[/IMG]**Case/Chassis**
JW CS-502B Black Deluxe Midi ATX Tower Case with 500W Power Supp


Only difference is that I removed the CD-ROM drive and replaced it with a 1TB hard drive from my old computer. I'm trying to make that my /home partition.

[/LIST]

---

### Post by fantab on 2013-12-20
> **sashin2 said:**
> 

Model: ATA WDC WD10EACS-00Z (scsi)
Disk /**dev/sda: 1000GB**
Sector size (logical/physical): 512B/512B
**Partition Table: msdos**

Number  Start   End    Size    Type     File system  Flags
 1      32.3kB  989GB  989GB   primary  ext4
 2      989GB   989GB  3146kB  primary


Model: ATA TOSHIBA DT01ACA0 (scsi)
Disk **/dev/sdb: 500GB**
Sector size (logical/physical): 512B/4096B
**Partition Table: gpt**

Number  Start   End    Size    File system     Name  Flags
 1      1049kB  498GB  498GB   ext4                  boot
 4      498GB   500GB  1999MB  linux-swap(v1)


Ubuntu, by default will install to /dev/sda or your WD-1 Tb, HDD. If you want to install Ubuntu to /dev/sdb or 500Gb HDD then you have to first change the HDD boot priority in your BIOS/UEFI to boot 500GB HDD first.

Check in the BIOS/UEFI and confirm if you have UEFI. Installing Ubuntu in UEFI needs some attention.
Ubuntu will only boot from GPT formatted disk in UEFI mode if the disk has an EFI partition... So its important that you tell us what you have.
You will probably have UEFI with an option to boot in 'legacy/MBR/CSM' mode.
If you ask me, then I'd say if you have UEFI install Ubuntu in UEFI mode only.

As we can see, your 500Gb HDD, /dev/sdb is formatted as GPT [GUID Partition Table]. 
For Ubuntu to boot from GPT in UEFI mode you will need a 500Mb EFI partition, formatted with FAT32 and a 'boot' flag.
For Ubuntu to boot from GPT in Legacy/CSM/BIOS/MBR mode you will need to make a 25Mb Unformatted partition with a 'bios_grub' flag.

500GB for '/' partition is ridiculously too much. For '/' partition about 25Gb is plenty.

---

### Post by sashin2 on 2013-12-20
Thanks for that! My bios indeed uses UEFI.  It's really late now, so I'll try that in the morning. So basically a 500MB partition that's EFI, FAT32 and has a boot flag. Does it matter which hard disk I put this partition on.

Also on a side note, what would you use the rest of the 500GB hard disk for?

---

### Post by fantab on 2013-12-20
Yes UEFI boot only works from GPT disk, which in your case is 500Gb HDD. So you HAVE to make an EFI partition on GPT Disk or 500Gb Disk.

If I were you I would partition the create 500gb (all partitions are PRIMARY in GPT):
300-500Mb FAT32 'boot' flag, EFI partition
25Gb Ext4 Ubuntu 13.10 '/' system files
25Gb Ext4 Free (If I want to try another distro or another Ubuntu version or distro)
4Gb LinuxSWAP (If you like Hibernating your system then SWAP size should be equal to or more than your RAM in GiB and not GB).
445Gb Ext4 Data Partition. (I don't use /home since I multiboot more than 2 distros and avoid either different /home's or shared /home, If you are booting only one OS then separate /home partition is recommended)

I suggest that you convert your 1Tb drive to GPT, as well. There are [Advantages with GPT]("https://wiki.archlinux.org/index.php/GPT#Advantages_of_GPT").
Again, if I were you:
500Mb FAT32 boot-flag EFI 
25Gb Ext4
25Gb Ext4
2-4Gb LinuxSWAP
All the remaining GB Ext4 DATA 

If you have two different HDDs then it will be a good idea to install another linux distro on the second HDD. In case any HDD fails you can still boot from the other. We just have to change the HDD boot order in UEFI/BIOS.
Even if you don't install another distro on it now just set up the HDD that way, keep your options open.

---

### Post by sashin2 on 2013-12-20
Thanks a lot, I've followed your advice and now have a fully functional Ubuntu install!

---

### Post by fantab on 2013-12-20
That's great.
If you are done here, then you can mark this thread as 'Solved' using Thread tools.

---

