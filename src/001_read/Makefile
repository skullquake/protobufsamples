CXX=g++
CXXFLAGS=\
	 `pkg-config --cflags protobuf`
LIBS=\
	 `pkg-config --libs protobuf`
SRC=./src/a.cpp
BIN=./bin/a
PROTOC=protoc
PROTOCSRCDIR=./src
PROTOCDSTDIR=./src
PROTOCSRCNAM=addressbook
PROTOCSRC=$(PROTOCSRCDIR)/$(PROTOCSRCNAM).proto
PROTOCTGT=\
	  $(PROTOCDSTDIR)/$(PROTOCSRCNAM).pb.cc\
	  $(PROTOCDSTDIR)/$(PROTOCSRCNAM).pb.h
all:$(BIN) $(PROTOCTGT)
$(BIN):$(SRC) $(PROTOCTGT)
	@mkdir -p $(@D)
	@$(CXX)\
		$(CXXFLAGS)\
		$(SRC)\
		$(PROTOCDSTDIR)/$(PROTOCSRCNAM).pb.cc\
		$(LIBS)\
		-o $(BIN)
$(PROTOCTGT):$(PROTOCSRC)
	@$(PROTOC)\
		-I=$(PROTOCSRCDIR)\
		--cpp_out=$(PROTOCDSTDIR)\
		$(PROTOCSRCDIR)/$(PROTOCSRCNAM).proto
.phony:\
	run\
	clean
run:
	$(BIN) ./res/a
clean:
	rm -r ./bin $(PROTOCTGT)
