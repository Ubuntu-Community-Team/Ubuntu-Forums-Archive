---
title: "cuda 6.5 opencv ubunru 14.014TLS"
date: 2014-11-21
forum: Installation &amp; Upgrades
---

### Post by souzou2 on 2014-11-21
Hello,  I have a problem on installing opencv 2.4.9 on a system with Ubuntu 14.04 64 bit and cuda 6.5. 
I install cuda 6.5 successfully , then I use this link to install openCV [http://www.sysads.co.uk/2014/05/install-opencv-2-4-9-ubuntu-14-04-13-10/](http://www.sysads.co.uk/2014/05/install-opencv-2-4-9-ubuntu-14-04-13-10/)
when installing opencv, I remark that it has problem in NCVPixelOperations.hpp , so I look in the internet [http://ubuntuforums.org/showthread.php?t=2244063](http://ubuntuforums.org/showthread.php?t=2244063)
I done the same changes but I still have the same problem :mad:

If any one have a solution, please help me because I m so stressed...

```

[ 45%] Building CXX object modules/ocl/CMakeFiles/opencv_perf_ocl.dir/perf/perf_match_template.cpp.o
nvcc warning : The 'compute_11', 'compute_12', 'compute_13', 'sm_11', 'sm_12', and 'sm_13' architectures are deprecated, and may be removed in a future release.
/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(51): error: expected an identifier

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(51): error: expected a type specifier

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(51): error: expected a ";"

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(60): warning: parsing restarts here after previous syntax error

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(61): error: expected an identifier

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(61): error: expected a type specifier

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(61): error: expected a ";"

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(70): warning: parsing restarts here after previous syntax error

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(71): error: TConvVec2Base is not a template

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(72): error: TConvVec2Base is not a template

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(73): error: TConvVec2Base is not a template

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(74): error: TConvVec2Base is not a template

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(75): error: TConvVec2Base is not a template

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(76): error: TConvVec2Base is not a template

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(77): error: TConvVec2Base is not a template

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(78): error: TConvVec2Base is not a template

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(79): error: TConvVec2Base is not a template

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(80): error: TConvVec2Base is not a template

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(81): error: TConvVec2Base is not a template

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(82): error: TConvVec2Base is not a template

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(83): error: TConvVec2Base is not a template

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(84): error: TConvVec2Base is not a template

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(85): error: TConvVec2Base is not a template

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(119): error: expected an identifier

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(119): error: expected a type specifier

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(119): error: expected a ";"

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(152): warning: parsing restarts here after previous syntax error

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(154): error: a template argument list is not allowed in a declaration of a primary template

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(162): error: a template argument list is not allowed in a declaration of a primary template

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(172): error: a template argument list is not allowed in a declaration of a primary template

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPyramid.cu(144): error: identifier "TConvVec2Base" is undefined
          detected during:
            instantiation of "void kernelDownsampleX2(T *, Ncv32u, T *, Ncv32u, NcvSize32u) [with T=uchar1]" 
(217): here
            instantiation of "void cv::gpu::device::pyramid::kernelDownsampleX2_gpu<T>(cv::gpu::PtrStepSzb, cv::gpu::PtrStepSzb, cudaStream_t) [with T=uchar1]" 
(225): here

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPyramid.cu(144): error: type name is not allowed
          detected during:
            instantiation of "void kernelDownsampleX2(T *, Ncv32u, T *, Ncv32u, NcvSize32u) [with T=uchar1]" 
(217): here
            instantiation of "void cv::gpu::device::pyramid::kernelDownsampleX2_gpu<T>(cv::gpu::PtrStepSzb, cv::gpu::PtrStepSzb, cudaStream_t) [with T=uchar1]" 
(225): here

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPyramid.cu(144): error: the global scope has no "TBase"
          detected during:
            instantiation of "void kernelDownsampleX2(T *, Ncv32u, T *, Ncv32u, NcvSize32u) [with T=uchar1]" 
(217): here
            instantiation of "void cv::gpu::device::pyramid::kernelDownsampleX2_gpu<T>(cv::gpu::PtrStepSzb, cv::gpu::PtrStepSzb, cudaStream_t) [with T=uchar1]" 
(225): here

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPyramid.cu(273): error: identifier "TConvVec2Base" is undefined
          detected during instantiation of "void cv::gpu::device::pyramid::kernelInterpolateFrom1_gpu<T>(cv::gpu::PtrStepSzb, cv::gpu::PtrStepSzb, cudaStream_t) [with T=uchar1]" 
(300): here

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPyramid.cu(273): error: type name is not allowed
          detected during instantiation of "void cv::gpu::device::pyramid::kernelInterpolateFrom1_gpu<T>(cv::gpu::PtrStepSzb, cv::gpu::PtrStepSzb, cudaStream_t) [with T=uchar1]" 
(300): here

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPyramid.cu(273): error: the global scope has no "TBase"
          detected during instantiation of "void cv::gpu::device::pyramid::kernelInterpolateFrom1_gpu<T>(cv::gpu::PtrStepSzb, cv::gpu::PtrStepSzb, cudaStream_t) [with T=uchar1]" 
(300): here

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPyramid.cu(273): error: incomplete type is not allowed
          detected during:
            instantiation of "void kernelInterpolateFrom1(T *, Ncv32u, NcvSize32u, T *, Ncv32u, NcvSize32u) [with T=uchar1]" 
(292): here
            instantiation of "void cv::gpu::device::pyramid::kernelInterpolateFrom1_gpu<T>(cv::gpu::PtrStepSzb, cv::gpu::PtrStepSzb, cudaStream_t) [with T=uchar1]" 
(300): here

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPyramid.cu(273): error: incomplete type is not allowed
          detected during:
            instantiation of "void kernelInterpolateFrom1(T *, Ncv32u, NcvSize32u, T *, Ncv32u, NcvSize32u) [with T=uchar3]" 
(292): here
            instantiation of "void cv::gpu::device::pyramid::kernelInterpolateFrom1_gpu<T>(cv::gpu::PtrStepSzb, cv::gpu::PtrStepSzb, cudaStream_t) [with T=uchar3]" 
(301): here

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPyramid.cu(273): error: incomplete type is not allowed
          detected during:
            instantiation of "void kernelInterpolateFrom1(T *, Ncv32u, NcvSize32u, T *, Ncv32u, NcvSize32u) [with T=uchar4]" 
(292): here
            instantiation of "void cv::gpu::device::pyramid::kernelInterpolateFrom1_gpu<T>(cv::gpu::PtrStepSzb, cv::gpu::PtrStepSzb, cudaStream_t) [with T=uchar4]" 
(302): here

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPyramid.cu(273): error: incomplete type is not allowed
          detected during:
            instantiation of "void kernelInterpolateFrom1(T *, Ncv32u, NcvSize32u, T *, Ncv32u, NcvSize32u) [with T=ushort1]" 
(292): here
            instantiation of "void cv::gpu::device::pyramid::kernelInterpolateFrom1_gpu<T>(cv::gpu::PtrStepSzb, cv::gpu::PtrStepSzb, cudaStream_t) [with T=ushort1]" 
(304): here

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPyramid.cu(273): error: incomplete type is not allowed
          detected during:
            instantiation of "void kernelInterpolateFrom1(T *, Ncv32u, NcvSize32u, T *, Ncv32u, NcvSize32u) [with T=ushort3]" 
(292): here
            instantiation of "void cv::gpu::device::pyramid::kernelInterpolateFrom1_gpu<T>(cv::gpu::PtrStepSzb, cv::gpu::PtrStepSzb, cudaStream_t) [with T=ushort3]" 
(305): here

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPyramid.cu(273): error: incomplete type is not allowed
          detected during:
            instantiation of "void kernelInterpolateFrom1(T *, Ncv32u, NcvSize32u, T *, Ncv32u, NcvSize32u) [with T=ushort4]" 
(292): here
            instantiation of "void cv::gpu::device::pyramid::kernelInterpolateFrom1_gpu<T>(cv::gpu::PtrStepSzb, cv::gpu::PtrStepSzb, cudaStream_t) [with T=ushort4]" 
(306): here

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPyramid.cu(273): error: incomplete type is not allowed
          detected during:
            instantiation of "void kernelInterpolateFrom1(T *, Ncv32u, NcvSize32u, T *, Ncv32u, NcvSize32u) [with T=float1]" 
(292): here
            instantiation of "void cv::gpu::device::pyramid::kernelInterpolateFrom1_gpu<T>(cv::gpu::PtrStepSzb, cv::gpu::PtrStepSzb, cudaStream_t) [with T=float1]" 
(308): here

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPyramid.cu(273): error: incomplete type is not allowed
          detected during:
            instantiation of "void kernelInterpolateFrom1(T *, Ncv32u, NcvSize32u, T *, Ncv32u, NcvSize32u) [with T=float3]" 
(292): here
            instantiation of "void cv::gpu::device::pyramid::kernelInterpolateFrom1_gpu<T>(cv::gpu::PtrStepSzb, cv::gpu::PtrStepSzb, cudaStream_t) [with T=float3]" 
(309): here

/home/souad/Bureau/opencv/opencv/opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPyramid.cu(273): error: incomplete type is not allowed
          detected during:
            instantiation of "void kernelInterpolateFrom1(T *, Ncv32u, NcvSize32u, T *, Ncv32u, NcvSize32u) [with T=float4]" 
(292): here
            instantiation of "void cv::gpu::device::pyramid::kernelInterpolateFrom1_gpu<T>(cv::gpu::PtrStepSzb, cv::gpu::PtrStepSzb, cudaStream_t) [with T=float4]" 
(310): here

42 errors detected in the compilation of "/tmp/tmpxft_00001d27_00000000-21_NCVPyramid.compute_35.cpp1.ii".
CMake Error at cuda_compile_generated_NCVPyramid.cu.o.cmake:266 (message):
  Error generating file
  /home/souad/Bureau/opencv/opencv/opencv-2.4.9/build/modules/gpu/CMakeFiles/cuda_compile.dir/src/nvidia/core/./cuda_compile_generated_NCVPyramid.cu.o


make[2]: *** [modules/gpu/CMakeFiles/cuda_compile.dir/src/nvidia/core/./cuda_compile_generated_NCVPyramid.cu.o] Erreur 1
make[1]: *** [modules/gpu/CMakeFiles/opencv_gpu.dir/all] Erreur 2
make[1]: *** Attente des tâches non terminées....
[ 45%] Building CXX object modules/ocl/CMakeFiles/opencv_perf_ocl.dir/perf/perf_split_merge.cpp.o
[ 45%] Building CXX object modules/ocl/CMakeFiles/opencv_perf_ocl.dir/perf/perf_filters.cpp.o
[ 45%] Building CXX object modules/ocl/CMakeFiles/opencv_perf_ocl.dir/perf/perf_matrix_operation.cpp.o
[ 46%] Building CXX object modules/ocl/CMakeFiles/opencv_perf_ocl.dir/perf/main.cpp.o
[ 46%] Building CXX object modules/ocl/CMakeFiles/opencv_perf_ocl.dir/perf/perf_canny.cpp.o
[ 46%] Building CXX object modules/ocl/CMakeFiles/opencv_perf_ocl.dir/perf/perf_gftt.cpp.o
[ 46%] Building CXX object modules/ocl/CMakeFiles/opencv_perf_ocl.dir/perf/perf_pyramid.cpp.o
[ 46%] Building CXX object modules/ocl/CMakeFiles/opencv_perf_ocl.dir/perf/perf_calib3d.cpp.o
[ 46%] Building CXX object modules/ocl/CMakeFiles/opencv_perf_ocl.dir/perf/perf_opticalflow.cpp.o
[ 46%] Building CXX object modules/ocl/CMakeFiles/opencv_perf_ocl.dir/perf/perf_bgfg.cpp.o
[ 46%] Building CXX object modules/ocl/CMakeFiles/opencv_perf_ocl.dir/perf/perf_haar.cpp.o
[ 46%] Building CXX object modules/ocl/CMakeFiles/opencv_perf_ocl.dir/perf/perf_color.cpp.o
[ 46%] Building CXX object modules/ocl/CMakeFiles/opencv_perf_ocl.dir/perf/perf_imgproc.cpp.o
[ 46%] Building CXX object modules/ocl/CMakeFiles/opencv_perf_ocl.dir/perf/perf_imgwarp.cpp.o
[ 46%] Building CXX object modules/ocl/CMakeFiles/opencv_perf_ocl.dir/perf/perf_blend.cpp.o
[ 46%] Building CXX object modules/ocl/CMakeFiles/opencv_perf_ocl.dir/perf/perf_hog.cpp.o
[ 46%] Building CXX object modules/ocl/CMakeFiles/opencv_perf_ocl.dir/perf/perf_ml.cpp.o
[ 47%] Building CXX object modules/ocl/CMakeFiles/opencv_perf_ocl.dir/perf/perf_stat.cpp.o
[ 47%] Building CXX object modules/ocl/CMakeFiles/opencv_perf_ocl.dir/perf/perf_fft.cpp.o
[ 47%] Building CXX object modules/ocl/CMakeFiles/opencv_perf_ocl.dir/perf/perf_gemm.cpp.o
[ 47%] Building CXX object modules/ocl/CMakeFiles/opencv_perf_ocl.dir/perf/perf_arithm.cpp.o
[ 47%] Building CXX object modules/ocl/CMakeFiles/opencv_perf_ocl.dir/perf/perf_moments.cpp.o
[ 47%] Building CXX object modules/ocl/CMakeFiles/opencv_perf_ocl.dir/perf/perf_brute_force_matcher.cpp.o
Linking CXX executable ../../bin/opencv_perf_ocl
[ 47%] Built target opencv_perf_ocl
make: *** [all] Erreur 2


```

---

### Post by bashiergui on 2014-11-22
This link states that there are often installation problems, so they have a script to use
[https://help.ubuntu.com/community/OpenCV](https://help.ubuntu.com/community/OpenCV)

---

