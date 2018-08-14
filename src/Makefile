CXX=clang++
#CXXFLAGS=-std=c++14 -fopenmp -O3 -march=native
CXXFLAGS=-std=c++14 -O3 -march=native
CXXFLAGS=-std=c++14 -O0 -g

# Boost
BOOST=/opt/local
BOOST_INCLUDE=$(BOOST)/include
BOOST_LIBRARIES=$(BOOST)/lib

# Eigen
EIGEN=/opt/local
EIGEN_INCLUDE=$(EIGEN)/include/eigen3

# TCLAP
TCLAP=/opt/local
TCLAP_INCLUDE=$(TCLAP)/include
TCLAP_LIBRARIES=$(TCLAP)/lib

# libpng
PNG=/opt/local
PNG_INCLUDE=$(PNG)/include
PNG_LIBRARIES=$(PNG)/lib

OBJS=atomicgrid.o cspline.o dftcxx.o gamma.o integrals.o molecule.o quadrature.o settings.o cgf.o dft.o \
     functionals.o gridpoint.o moleculargrid.o pngfuncs.o rectangulargrid.o spherical_harmonics.o

dftcxx : $(OBJS)
	$(CXX) $(CXXFLAGS) -L$(BOOST_LIBRARIES) -L$(TCLAP_LIBRARIES) -L$(PNG_LIBRARIES) \
	$^ -o $@ -lboost_regex-mt -lboost_iostreams-mt -lboost_filesystem-mt -lboost_system-mt -lpng

%.o : %.cpp
	$(CXX) $(CXXFLAGS) -c -I$(BOOST_INCLUDE) -I$(EIGEN_INCLUDE) -I$(TCLAP_INCLUDE) -I$(PNG_INCLUDE) \
	$< -o $@

clean :
	rm -f *.o

veryclean :
	rm -f *.o dftcxx

