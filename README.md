# APQF

**Agentic Profiling-Guided Structured Pruning and Mixed-Precision Quantization with Adaptive Fine-Tuning**

APQF is an agentic framework for compressing vision models through profiling-guided structured pruning, mixed-precision quantization-aware training, and adaptive accuracy recovery. The framework uses measured model profiles to guide LLM planners in selecting model-specific pruning ratios, quantization bit-widths, and fine-tuning strategies.

APQF supports both convolutional neural networks and vision transformers. It has been evaluated on ResNet, VGG, ViT, DeiT, and Swin models using ImageNet-1K and CIFAR-10.

## Resources

- [Paper on arXiv](https://arxiv.org/abs/2608.05499)
- [SC26 poster](APQF_SC26_Poster.pdf)

## Framework Overview

APQF coordinates five specialized components:

1. **ProfilingAgent** measures model cost and the pruning sensitivity of structural dependency groups.
2. **PrunerAgent** performs LLM-guided, multi-stage structured pruning toward a target parameter reduction.
3. **FineTuningAgent** selects adaptive recovery strategies after pruning and quantization.
4. **QuantAgent** assigns per-layer bit-widths and performs mixed-precision quantization-aware training with knowledge distillation.
5. **EvaluationAgent** measures accuracy, parameter reduction, model size, and relative bit-operations under a shared evaluation protocol.

## Highlights

- Profiling-grounded compression decisions instead of uniform layer settings.
- Per-group structured pruning ratios selected from measured sensitivity data.
- Per-layer mixed-precision assignments for weights and activations.
- Adaptive PEFT, full fine-tuning, and knowledge-distillation recovery.
- A common pipeline for CNN and transformer architectures.
- Support for different commercial and open-weight LLM planners through OpenRouter.

On ImageNet-1K, APQF reduces relative bit-operations to approximately 5.6-7.7% of the original FP32 models. On VGG7/CIFAR-10, it achieves 93.15% Top-1 accuracy at 0.41% relative bit-operations and 92.68% at 0.36% relative bit-operations.

## Code Availability

This public repository currently contains the project description and poster only. The APQF implementation is being kept private during the conference submission and review process. The source code and reproducibility instructions will be released following acceptance of the conference paper.

## Citation

If you use or discuss APQF, please cite the arXiv paper:

```bibtex
@article{jafari2026apqf,
  title={APQF: Agentic Profiling-Guided Structured Pruning and Mixed-Precision Quantization with Adaptive Fine-Tuning},
  author={Jafari, Sadegh and Bilwal, Mohiuddin and Zhou, Fan and Gelder, Brian and Jannesari, Ali},
  journal={arXiv preprint arXiv:2608.05499},
  year={2026}
}
```

## Authors

- Sadegh Jafari
- Mohiuddin Bilwal
- Fan Zhou
- Brian Gelder
- Ali Jannesari

Iowa State University

For questions about APQF, contact [Sadegh Jafari](mailto:sadegh@iastate.edu).
