---
title: "Upgrading to Ubuntu 18.04 mouse jerking issues while Einstein at Home is running -GPU"
date: 2018-04-28
forum: Installation &amp; Upgrades
---

### Post by thinkingbeyondthesquare on 2018-04-28
Hi Team


  Not sure whats going on. 

Had Einstein working fine on my AMD RX480 with Ubuntu 17.10.


  Yesterday I upgraded to the latest Ubuntu 18.04 and now when I have  Einstein running the mouse/screen display will temporarily freeze for half a second and  it repeats this every 3 to 5 seconds. Naturally this makes using the  computer impossible lol.


  When I disabled Einstein at Home the pc works as usual.

Quick Note: Einstein at Home is a distributed computer platform using my CPU and GPU, via OpenCL to perform work.


    The issue is occurring under both Wayland and X11.


I am running the latest OpenCL stack/drivers on the GPU.


  I am not only running the latest open source AMD/Mesa stack drivers  from Ubuntu 18.04 but have gone one step over and installed the bleeding  edge oibaf drivers to try and sort the issue.


  [URL="https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers"]https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers

[/URL]

  I also manually installed the latest OpenCL driver: 

"sudo apt install mesa-opencl-icd"

The problem still persists.


Boinc's log shows that it sees my GPU and lists its OpenCL attributes as well.


  The pause of the mouse is also temporarily pausing the PC as well.  Its more like a graphical 'glitch' that freezes the screen. The  underlying subsystems hums along under the glitch with no issues.


  I have an 8 core, 16 thread Ryzen CPU, even with it running 4 other  boinc tasks it is no where near full capacity (about 35% utilisation in  fact).


  Suspending Einstein at Home returns the PC to normal operation.


  The PC ran this setup fluidly under Ubuntu 17.10

   
  byw/FYI my clinfo output is:
Number of platforms                               1
  Platform Name                                   Clover
  Platform Vendor                                 Mesa
  Platform Version                                OpenCL 1.1 Mesa 18.2.0-devel
  Platform Profile                                FULL_PROFILE
  Platform Extensions                             cl_khr_icd
  Platform Extensions function suffix             MESA
    Platform Name                                   Clover
Number of devices                                 1
  Device Name                                     AMD Radeon (TM) RX 480  Graphics (POLARIS10, DRM 3.23.0, 4.15.0-20-generic, LLVM 6.0.0)
  Device Vendor                                   AMD
  Device Vendor ID                                0x1002
  Device Version                                  OpenCL 1.1 Mesa 18.2.0-devel
  Driver Version                                  18.2.0-devel
  Device OpenCL C Version                         OpenCL C 1.1
  Device Type                                     GPU
  Device Profile                                  FULL_PROFILE
  Device Available                                Yes
  Compiler Available                              Yes
  Max compute units                               36
  Max clock frequency                             1342MHz
  Max work item dimensions                        3
  Max work item sizes                             256x256x256
  Max work group size                             256
  Preferred work group size multiple              64
  Preferred / native vector sizes                 
    char                                                16 / 16      
    short                                                8 / 8       
    int                                                  4 / 4       
    long                                                 2 / 2       
    half                                                 8 / 8        (cl_khr_fp16)
    float                                                4 / 4       
    double                                               2 / 2        (cl_khr_fp64)
  Half-precision Floating-point support           (cl_khr_fp16)
    Denormals                                     No
    Infinity and NANs                             Yes
    Round to nearest                              Yes
    Round to zero                                 No
    Round to infinity                             No
    IEEE754-2008 fused multiply-add               No
    Support is emulated in software               No
  Single-precision Floating-point support         (core)
    Denormals                                     No
    Infinity and NANs                             Yes
    Round to nearest                              Yes
    Round to zero                                 No
    Round to infinity                             No
    IEEE754-2008 fused multiply-add               No
    Support is emulated in software               No
    Correctly-rounded divide and sqrt operations  No
  Double-precision Floating-point support         (cl_khr_fp64)
    Denormals                                     Yes
    Infinity and NANs                             Yes
    Round to nearest                              Yes
    Round to zero                                 Yes
    Round to infinity                             Yes
    IEEE754-2008 fused multiply-add               Yes
    Support is emulated in software               No
  Address bits                                    64, Little-Endian
  Global memory size                              8587018240 (7.997GiB)
  Error Correction support                        No
  Max memory allocation                           6010912768 (5.598GiB)
  Unified memory for Host and Device              No
  Minimum alignment for any data type             128 bytes
  Alignment of base address                       32768 bits (4096 bytes)
  Global Memory cache type                        None
  Image support                                   No
  Local memory type                               Local
  Local memory size                               32768 (32KiB)
  Max number of constant args                     16
  Max constant buffer size                        2147483647 (2GiB)
  Max size of kernel argument                     1024
  Queue properties                                
    Out-of-order execution                        No
    Profiling                                     Yes
  Profiling timer resolution                      0ns
  Execution capabilities                          
    Run OpenCL kernels                            Yes
    Run native kernels                            No
  Device Extensions                                cl_khr_byte_addressable_store cl_khr_global_int32_base_atomics  cl_khr_global_int32_extended_atomics cl_khr_local_int32_base_atomics  cl_khr_local_int32_extended_atomics cl_khr_int64_base_atomics  cl_khr_int64_extended_atomics cl_khr_fp64 cl_khr_fp16
  NULL platform behavior
  clGetPlatformInfo(NULL, CL_PLATFORM_NAME, ...)  Clover
  clGetDeviceIDs(NULL, CL_DEVICE_TYPE_ALL, ...)   Success [MESA]
  clCreateContext(NULL, ...) [default]            Success [MESA]
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_DEFAULT)  Success (1)
    Platform Name                                 Clover
    Device Name                                   AMD Radeon (TM) RX 480  Graphics (POLARIS10, DRM 3.23.0, 4.15.0-20-generic, LLVM 6.0.0)
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_CPU)  No devices found in platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_GPU)  Success (1)
    Platform Name                                 Clover
    Device Name                                   AMD Radeon (TM) RX 480  Graphics (POLARIS10, DRM 3.23.0, 4.15.0-20-generic, LLVM 6.0.0)
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_ACCELERATOR)  No devices found in platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_CUSTOM)  No devices found in platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_ALL)  Success (1)
    Platform Name                                 Clover
    Device Name                                   AMD Radeon (TM) RX 480  Graphics (POLARIS10, DRM 3.23.0, 4.15.0-20-generic, LLVM 6.0.0)
  ICD loader properties
  ICD loader Name                                 OpenCL ICD Loader
  ICD loader Vendor                               OCL Icd free software
  ICD loader Version                              2.2.11
  ICD loader Profile                              OpenCL 2.1
 

Any ideas would be appreciated.


  Cheers
   
  Mark

---

